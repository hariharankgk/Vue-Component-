<template>
  <div id="app">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <img alt="Vue logo" src="./assets/logo.png">
    <BackToTop></BackToTop>
    <ul class="socialshare">
      <li v-for="(j, index) in myJson" :key="index">
        <social-sharing url="www.google.com" inline-template>
          <div>
              <network :network="index">
                <i :class="'fa fa-fw fa-' + index"></i> {{index}}
              </network>
          </div>
        </social-sharing>
      </li>
    </ul>
    <br/>
    <ul class="product-list">
      <li v-for="(p, index) in productslist" :key="index">
        <Favourite :lists="p" :fav="favourites"></Favourite>
        <div class="image"></div>
        <p>{{p.name}}</p>
      </li>
    </ul>
    <br/>
    <collections></collections>
  </div>
</template>

<script>
import SocialSharing from './social-sharing';
import BackToTop from './components/scrolltop';
import Favourite from './components/favourites';
import collections from './components/collections';
import json from './networks.json'
import products from './products.json'
// import { EventBus } from "./event-bus.js";
export default {
  name: 'App',
  components: {
    SocialSharing,
    BackToTop,
    Favourite,
    collections
  },
  data(){
    return {
      myJson: json,
      productslist: products,
      favourites: []
    }
  },
  mounted(){
    window.scrollTo(0,0);
  },
  methods: {
    addToFavourites: function(){
      console.log('parent');
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  min-height:200vh;
}
.socialshare {
  list-style-type: none;
  padding:0;
  display:flex;
  justify-content: center;

}
.socialshare li{
  display: inline-block;
  margin:0 10px;
  cursor: pointer;
}

.product-list {
  width:75%;
  margin:auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.product-list li {
  min-height:200px;
  list-style-type: none;
  border: 1px solid #ddd;
  flex:1 1 0;
  margin: 0 10px;
  position: relative;
}
.product-list li .image {
  min-height:150px;
}
</style>
