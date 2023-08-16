<template>
  <div>
    <div>
      <div class="font-bold">1. Display product information</div>
      <input type="number" style="border: 1px solid grey" v-model="productID" />
      <button
        style="background-color: green; border-radius: 10px"
        class="ml-5 p-1 text-white"
        @click="displayProduct"
      >
        Search Product
      </button>
    </div>
    <div class="flex justify-center">
      <div style="border: 1px solid green" class="mt-2 w-96 h-96">
        {{ ProductSearched.id }}, {{ ProductSearched.name }},
        {{ categorySearched.name }}
      </div>
    </div>

    <br />
    <div>
      <div>
        <div class="font-bold">2. Display Related Product</div>
        <input
          type="number"
          style="border: 1px solid grey"
          v-model="category"
        />
        <button
          style="border-radius: 10px; background-color: green"
          class="p-1 ml-5 text-white"
          @click="productRelated"
        >
          Search Related Product
        </button>
      </div>
      <div class="flex justify-center">
        <div style="border: 1px solid green" class="mt-2 w-96 h-96">
          <div v-for="(item, i) in relatedProducts" :key="i">
            {{ item.id }}, {{ item.name }} , {{ categorySearched.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        { id: 1, name: "Dell", category_id: 101 },
        { id: 2, name: "Power Supply", category_id: 102 },
        { id: 3, name: "Macbook", category_id: 101 },
        { id: 4, name: "Monitor", category_id: 103 },
        { id: 5, name: "Keyboard", category_id: 104 },
        { id: 6, name: "Mouse", category_id: 104 },
        { id: 7, name: "Headphones", category_id: 105 },
      ],
      categories: [
        { id: 101, name: "Computers" },
        { id: 102, name: "Power Supplies" },
        { id: 103, name: "Monitors" },
      ],
      ProductList: [],
      productID: "",
      ProductSearched: {},
      categorySearched: {},
      category: "",
      item: [],
      item1: [],

      // Question 2
      relatedProducts: [],
    };
  },
  created() {
    this.displayProduct();
    this.productRelated();
  },
  methods: {
    // Solution 1
    displayProduct() {
      for (let i = 0; i < this.products.length; i++) {
        if (parseInt(this.products[i].id) === this.productID) {
          this.ProductSearched = this.products[i];
          console.log("final product:", this.ProductSearched);
          this.categorySearched = this.categories[i];
          console.log("final category: ", this.categorySearched);
          break;
        }
      }
    },

    // Solution2
    productRelated() {
      this.relatedProducts = [];
      for (let i = 0; i < this.products.length; i++) {
        if (parseInt(this.products.id) === this.category) {
          this.ProductSearched = this.products[i];
          this.categorySearched = this.categories[i];
        }
      }
      for (let i = 0; i < this.products.length; i++) {
        if (this.products[i].category_id === this.categorySearched.id) {
          this.relatedProducts.push(this.products[i]);
          console.log("ex2:", this.relatedProducts);
        }
      }
    },
  },
};
</script>

<style scoped></style>
