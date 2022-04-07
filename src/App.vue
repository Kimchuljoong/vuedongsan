<template>
  <div id="app">

    <div class="menu">
      <a>Home</a>
      <a>Products</a>
      <a>About</a>
    </div>

    <Discount v-if="showDiscount" />

    <transition name="fade">
      <Modal v-bind:product="products[modalProduct]" v-bind:showModal="showModal" v-on:setShowModal="showModal = false;" />
    </transition>
<!--    <div class="start" :class="{ end : showModal }" >-->
<!--    <Modal v-bind:product="products[modalProduct]" v-bind:showModal="showModal" v-on:setShowModal="showModal = false;" />-->
<!--    </div>-->

    <button v-on:click=priceSort>가격순정렬</button>
    <button v-on:click=sortBack>되돌리기</button>

    <Card v-for="(product, i) in products" :key="i" v-bind:product="product" v-bind:showModal="showModal" v-on:setShowModal="showModal = true; modalProduct = $event;"/>
<!--    <Card v-bind:product="products[0]"/>-->
<!--    <div v-for="(product, i) in products" :key="i" class="product" v-on:click="showModal = true; modalProduct=i;">-->
<!--      <img :src="product.image" class="room-img"/>-->
<!--      <h4 v-on:click="showModal=true">{{product.title}}</h4>-->
<!--      <p>{{product.price}}원</p>-->
<!--    </div>-->

  </div>
</template>

<script>

import data from './assets/oneroom.js';
import Discount from "./components/Discount";
import Modal from "./components/Modal";
import Card from "./components/Card";

export default {
  name: 'App',
  data(){
    return {
      oriProducts : [...data],
      products : [...data],
      modalProduct : 0,
      showModal : false,
      showDiscount : true,
      singo : [0, 0, 0],
    }
  },
  methods: {
    increase(i) {
      this.$set(this.singo,i,this.singo[i]+1);
    },
    priceSort() {
      this.products.sort((a, b) => {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.products = [...this.oriProducts];
    }
  },
  created() {

  },
  mounted() {
    setTimeout(() => {
      this.showDiscount = false;
    }, 3000);
  },
  components: {
    Card : Card,
    Modal: Modal,
    Discount: Discount,
  }
}
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

body {
  margin: 0;
  padding: 0;
}

div {
  box-sizing: border-box;
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
  position: relative;
}

.menu a {
  color: white;
  padding: 10px;
}

.start {
  opacity: 0;
  transition: all 0.25s;
}

.end {
  opacity: 1;
}

</style>
