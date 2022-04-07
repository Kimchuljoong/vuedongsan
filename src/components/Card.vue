<template>
  <div class="card">
    <img :src="product.image" class="room-img"/>
    <h4 v-on:click="$emit('setShowModal', product.id)">{{product.title}}</h4>
    <p>{{product.price}}원</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props:{
    product: Object,
  },
}
</script>

<style scoped>

.room-img {
  width: 100%;
}

.card {
  margin-top: 20px;
  margin-bottom: 20px;
}

</style>