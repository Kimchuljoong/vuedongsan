<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <img :src="product.image" style="width:100%"/>
      <h4>{{ product.title }}</h4>
      <p>{{ product.content }}</p>
      <input v-on:input="month = $event.target.value" :value="month"/>
      <p> {{ month }}개월 선택함 : {{ product.price * month }}</p>
      <button v-on:click="$emit('setShowModal')">닫 기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 1,
    }
  },
  watch: {
    month(e) {
      if(isNaN(e)){
        alert("숫자만 입력해야합니다.");
        this.month = 1;
      }
    },
  },
  props: {
    product: Object,
    showModal: Boolean,
  },
}
</script>

<style scoped>

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  top:0;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  margin-top: 30px;
  padding: 20px;
}

</style>