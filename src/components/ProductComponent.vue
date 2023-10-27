<template>
  <div v-if="product" class="container">
    <div class="img-section">
      <img :src="this.product.image" />
    </div>
    <div class="content-section">
      <div>
        <h1 :style="`color: ${switchColor}`">
          {{ this.product.title }}
        </h1>
        <div
          class="flex justify-between item-center"
          style="
            padding: 14px 0;
            border-bottom: 2px solid var(--light-gray-color);
            margin-top: 10px;
          "
        >
          <p>{{ this.product.category }}</p>
          <div class="flex item-center" style="gap: 2px">
            <p style="margin-right: 2px">{{ this.product.rating.rate }}/5</p>
            <span
              v-for="index in Math.ceil(this.product.rating.rate)"
              :key="'rate-' + index"
              :style="`
                width: 14px;
                height: 14px;
                background-color: ${switchColor};
                border-radius: 100%;`"
            ></span>
            <span
              v-for="index in 5 - Math.ceil(this.product.rating.rate)"
              :key="'norate-' + index"
              :style="`
                width: 14px;
                height: 14px;
                border: 1px solid ${switchColor};
                border-radius: 100%;`"
            ></span>
          </div>
        </div>
        <p style="padding: 20px 0">
          {{ this.product.description }}
        </p>
        <p
          :style="`
            font-size: 28px;
            font-weight: bold;
            color: ${switchColor};
            padding: 14px 0;
            margin-top: 20px;
            border-top: 2px solid var(--light-gray-color);`"
        >
          ${{ this.product.price }}
        </p>
        <div class="flex" style="gap: 12px">
          <button
            :style="`
              width: 100%;
              padding: 12px 0;
              border: none;
              background-color: ${switchColor};
              color: white;
              font-size: larger;
              cursor: pointer;`"
          >
            Buy Now
          </button>
          <button
            :style="`
              width: 100%;
              padding: 12px 0;
              border: 4px solid ${switchColor};
              background-color: transparent;
              color: ${switchColor};
              font-size: larger;
              font-weight: bold;
              cursor: pointer;`"
            @click="getNextProduct"
            :disabled="loading"
          >
            {{ loading ? "Loading..." : "Next Product" }}
          </button>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <skeleton-component></skeleton-component>
  </div>
</template>

<script>
import SkeletonComponent from "./SkeletonComponent.vue";

export default {
  name: "ProductComponent",
  components: {
    "skeleton-component": SkeletonComponent,
  },
  data() {
    return {
      product: null,
      id: 1,
      loading: false,
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      this.loading = true;
      try {
        const response = await fetch(
          `https://fakestoreapi.com/products/${this.id}`
        );
        const data = await response.json();

        const categories = ["men's clothing", "women's clothing"];
        if (categories.includes(data.category)) {
          this.product = data;
          this.sendDataToParent();
        } else {
          this.product = null;
          this.getNextProduct();
        }
      } catch (error) {
        console.error("Error fetching data:", error);
      } finally {
        this.loading = false;
      }
    },
    getNextProduct() {
      if (this.id === 20) {
        this.id = 1;
      } else {
        this.id++;
      }
      this.fetchData();
    },
    sendDataToParent() {
      // Assuming this.product contains the data you want to send
      this.$emit("product-data-to-parent", this.product);
    },
  },
  computed: {
    switchColor() {
      if (this.product.category === "women's clothing") {
        return "var(--secondary-color)";
      } else {
        return "var(--primary-color)";
      }
    },
  },
};
</script>

<style scoped>
img {
  width: 100%;
  height: 100%;
  aspect-ratio: initial;
}
h1 {
  font-size: 30px;
}
.container {
  display: flex;
  justify-content: space-between;
  width: 100%;
  min-height: 70vh;
  max-width: 900px;
  gap: 32px;
  background-color: white;
  padding: 40px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.4);
}

.img-section {
  min-width: 250px;
  width: 100%;
  height: 100%;
  max-width: 250px;
}

.flex {
  display: flex;
}

.justify-between {
  justify-content: space-between;
}

.item-center {
  align-items: center;
}
</style>
