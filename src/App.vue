<template>
  <div id="app">

    <div class="menu">
      <a>Home</a>
      <a>Products</a>
      <a>About</a>
    </div>

    <div v-for="(product, i) in products" :key="i">
      <h4>{{product[0]}}</h4>
      <p>{{product[1]}} 만원</p>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      products : [['역삼역원룸', 50], ['천호동원룸', 60], ['마포구원룸', 70]]
    }
  },
  components: {

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

</style>
