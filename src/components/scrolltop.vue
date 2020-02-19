<template>
    <div>
        <div v-if="showBTop">
            <a class="back_to_top" href="javascript:void(0)" @click="toTop"> <i class="fa fa-chevron-up"></i><br/>Back<br/>to<br/>Top</a>
        </div>
    </div>
</template>
<script>
export default {
  name: 'BackToTop',
  data(){
    return {
     scrollPosition: null,
     showBTop: false   
    }
  },
  methods:{
    toTop: function(){
        window.scrollTo(0,0);
    },
    updateScroll() {
      this.scrollPosition = window.scrollY;
      if(this.scrollPosition > 400){
        this.showBTop = true;
      } else {
          this.showBTop = false;
      }
    }
  },
  mounted() {
    window.addEventListener('scroll', this.updateScroll);
    window.scrollTo(0,0);
  }
  
}
</script>

<style>
    .back_to_top{
        position: fixed;
        top:60%;
        left:90%;
        padding: 10px;
        background-color: lightgray;
        color: #000;
        text-decoration: none;
        font-size: 12px;
        text-transform: uppercase;
    }
</style>