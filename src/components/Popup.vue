<template>
  <div class="parent-popup">
    <div id="popup-content">
      <button class="close" @click="onClose()">X</button>
      <img
        :src="product.image"
        width="350px"
        height="450px"
        :id="product.id"
        :key="product.id"
      />
      <div>
        <h1>{{ product.title }}</h1>
        <h4>Description</h4>
        <p id="popup-desc">
          {{ product.description }}
        </p>
        <button @click="sendProductToCart()">Lägg till</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Popup",

  props: {
    product: Object,
  },
  methods: {
    onClose() {
      this.$emit("close-Popup");
      
    },
    sendProductToCart() {
      this.$emit("send-Product");
    },
  },
};
</script>

<style scoped>
/* POPUP */

.parent-popup {
  display: flex;
  align-items: center;
  justify-content: center;
}
#popup-content {
  display: block;
  background: rgb(255, 255, 255);
  width: 400px;
  position: fixed;
  border: 2px solid rgb(172, 169, 169);
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.popUp {
  display: block;
  width: 300px;
  height: 300px;
  border: 2px solid rgb(0, 0, 0);
}
</style>
