<template>
    <div>
        <div class="carousel">
            <carousel :per-page="4" :mouse-drag="false" :paginationEnabled="false" :navigationEnabled="true">
                <slide v-for="(item, index) in collectionlist" :key="index" spacePadding="10px">
                <img :src="require('../assets/'+item.image)" alt="item.name">
                <h5>{{item.name}}</h5>
                <p>{{item.price}}</p>
                </slide>
            </carousel>
        </div>
    </div>
</template>
<script>
import alsocollections from './../collectionlist.json'

export default {
  name: 'Collections',
  data(){
    return {
     collectionlist: alsocollections
    }
  }
}
</script>

<style>
    .carousel {
        width:80%;
        margin:100px auto 0;
    }
    .carousel img {
        max-width:100%;
        max-height:300px;
    }
    .carousel h5 {
        margin:0;
        text-align: left;
        margin-bottom: 5px;
    }
    .carousel p {
        margin:0;
        text-align: left;
        font-size:13px;
        color:rgba(0,0,0,0.7);
    }
    .VueCarousel-slide {
        text-align: left;
        padding-right:5px;
    }
</style>