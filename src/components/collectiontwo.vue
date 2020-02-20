<template>
    <div>
        <div class="carousel">
            <vueper-slides class="no-shadow"
                :visible-slides="3"
                slide-multiple
                :gap="3"
                :slide-ratio="1 / 4"
                :dragging-distance="200"
                :bullets="false"
                :arrowsOutside="false"
                :breakpoints="{ 800: { visibleSlides: 2, slideMultiple: 2 } }">
                <vueper-slide v-for="(item, index) in collectionlist" :key="index" :title="item.name">
                     <template v-slot:content>
                        <a :href="require('../assets/'+item.image)">
                            <img :src="require('../assets/'+item.image)" alt="item.name">
                            <h5>{{item.name}}</h5>
                            <p>{{item.price}}</p>
                        </a>
                    </template>
                </vueper-slide>
            </vueper-slides>
        </div>
    </div>
</template>
<script>
import { VueperSlides, VueperSlide } from 'vueperslides'
import 'vueperslides/dist/vueperslides.css'
import alsocollections from './../collectionlist.json'


export default {
  name: 'Collections',
  components: {
      VueperSlides, 
      VueperSlide
  },
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
    .carousel a {
        text-decoration: none;
        color:#000;
    }
    .VueCarousel-slide {
        text-align: left;
        padding-right:5px;
    }
</style>