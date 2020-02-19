<template>
    <div>
        <div class="favourite-box">
            <span class="favourite"><i :class="{'fa fa-heart-o' : !favcheck, 'fa fa-heart' : favcheck}"></i></span>
            <input type="checkbox" class="checkbox" v-model="favcheck"  @change="addToFav">
        </div>
    </div>
</template>
<script>
export default {
    name: 'Favourites',
    data(){
        return {
            items: [],
            favcheck: false
        }
    },
    props: ['lists'],
    methods: {
        addToFav: function(){
            console.log(this.favcheck);
            if(this.favcheck == true) {
                this.items.push(this.lists);
                window.localStorage.setItem("favourites", JSON.stringify(this.items))
            } else {
                window.localStorage.removeItem("favourites");
            }
        }
    },
    created() {
        let val = JSON.parse(window.localStorage.getItem('favourites')) || [];
        if(val.length > 0){
            this.favcheck = val.filter(x => { return x.id === this.lists.id }).length > 0;
        } else {
            this.favcheck = false;
        }
    }
}

</script>

<style>
    .favourite{
        position: absolute;
        top:10px;
        right:10px;
        color: red;
        font-size: 14px;
    }
    .favourite-box {
        position: relative;
    }
    .checkbox {
        margin: 0;
        position: absolute;
        top: 10px;
        right: 10px;
        opacity: 0;
        cursor: pointer;
    }
</style>