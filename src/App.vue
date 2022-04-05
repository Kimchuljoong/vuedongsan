<template>
  <div id="app">

    <div class="menu">
      <a>Home</a>
      <a>Products</a>
      <a>About</a>
    </div>

    <div class="black-bg" v-if="showModal" v-on:click="showModal=false" >
      <div class="white-bg">
        <h4>{{ products[modalProduct].title }}</h4>
        <p>{{ products[modalProduct].content }}</p>
      </div>
    </div>

    <div v-for="(product, i) in products" :key="i" class="product" v-on:click="showModal = true; modalProduct=i;">
      <img :src="product.image" class="room-img"/>
      <h4 v-on:click="showModal=true">{{product.title}}</h4>
      <p>{{product.price}}원</p>
    </div>

  </div>
</template>

<script>

import data from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return {
      products : data,
      modalProduct : 0,
      showModal : false,
      singo : [0, 0, 0],

    }
  },
  methods: {
    increase(i) {
      this.$set(this.singo,i,this.singo[i]+1);
    }
  },

  components: {

  }
}
</script>

<style>

body {
  margin: 0;
  padding: 0;
}

div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;

  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
}

.product {
  margin-top: 40px;
  margin-bottom: 40px;
}

</style>
