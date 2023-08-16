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
        {{ ProductSearched }}
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
          @click="searchRelatedProduct"
        >
          Search Related Product
        </button>
      </div>
      <div class="flex justify-center">
        <div style="border: 1px solid green" class="mt-2 w-96 h-96">
          {{ relatedProducts }}
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
      ProductSearched: [],
      category: "",

      // Question 2
      relatedProducts: [],
    };
  },
  created() {
    this.displayProduct();
    this.searchRelatedProduct();
  },
  methods: {
    displayProduct() {
      this.ProductList = this.products;
      console.log("List Products: ", this.ProductList);
      for (let i = 0; i < this.ProductList.length; i++) {
        if (parseInt(this.ProductList[i].id) === this.productID) {
          this.ProductSearched.push(this.ProductList[i]);
        }
      }
    },
    searchRelatedProduct() {
      for (let i = 0; i < this.ProductList.length; i++) {
        if (parseInt(this.ProductList[i].category_id) === this.category) {
          return this.relatedProducts.push(this.ProductList[i]);
        }
      }
      console.log("Related Product:", this.relatedProducts);
    },
  },
};
</script>

<style scoped></style>
