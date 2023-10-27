<template>
  <div id="app">
    <div id="bg-container" :style="`background-color: ${switchColor}`"></div>
    <product-component @product-data-to-parent="receiveProductData" />
  </div>
</template>

<script>
import ProductComponent from "./components/ProductComponent.vue";

export default {
  name: "App",
  components: {
    "product-component": ProductComponent,
  },
  data() {
    return {
      product: null,
    };
  },
  methods: {
    // Define a method to handle the received product data
    receiveProductData(productData) {
      this.product = productData;
      // Now you can use the product data in your parent component
    },
  },
  computed: {
    switchColor() {
      if (this.product) {
        if (this.product.category === "women's clothing") {
          return "var(--pink-color)";
        } else {
          return "var(--sky-color)";
        }
      } else {
        return "var(--sky-color)";
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  min-height: 100vh;
  max-width: 1280px;
}
#bg-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 70vh;
  z-index: -1;
}
</style>
