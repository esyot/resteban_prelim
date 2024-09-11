<template>
    <div class="flex">
      <div class="w-1/2 p-2">
        <h1>All Items:</h1>
        <div v-for="item in items" :key="item.name" class="flex w-64 flex-col bg-gray-200 m-2 rounded">
          <div class="p-2">
            <h1>Product Name:</h1>
            {{ item.name }}
            <div class="flex">
              <h1>Price:</h1>
              <p>{{ item.price }}</p>
            </div>
            <div class="flex">
              <h1>Quantity:</h1>
              <p>{{ item.quantity }}</p>
            </div>
            <button v-if="item.isVisible" @click="handleAddToCart(item)" class="bg-blue-500 text-blue-100 px-4 py-2 rounded">Add</button>
          </div>
        </div>
      </div>
  
      <div class="w-1/2 p-2">
        <h1>Visible Items:</h1>
        <div v-for="item in visibleItems" :key="item.name" class="flex w-64 flex-col bg-blue-200 m-2 rounded">
          <div class="p-2">
            <h1>Product Name:</h1>
            {{ item.name }}
            <div class="flex">
              <h1>Price:</h1>
              <p>{{ item.price }}</p>
            </div>
            <div class="flex">
              <h1>Quantity:</h1>
              <p>{{ item.quantity }}</p>
            </div>
            <button @click="handleAddToCart(item)" class="bg-blue-500 text-blue-100 px-4 py-2 rounded">Add</button>
          </div>
        </div>
      </div>
    </div>
  
    <div>
      <h1>Computed Items:</h1>
      Total Price: ₱{{ totalPrice }}
    </div>
  </template>
  
  <script>
  export default {
    name: "ItemsList",
    data() {
      return {
        items: [
          { name: "Camia", description: "Rice", quantity: 12, price: 12, isVisible: true },
          { name: "Datu Puti", description: "Food & Beverages", quantity: 12, price: 13, isVisible: true },
          { name: "Datu Puti Soy Sauce", description: "Food & Beverages", quantity: 12, price: 14, isVisible: true }
        ]
      };
    },
    methods: {
      handleAddToCart(item) {
        item.isVisible = false;
      }
    },
    computed: {
      visibleItems() {
        return this.items.filter(item => item.isVisible);
      },
      totalPrice() {
        return this.visibleItems.reduce((total, item) => total + item.price, 0);
      }
    }
  };
  </script>
  
  <style scoped>
  .flex {
    display: flex;
  }
  .p-2 {
    padding: 8px;
  }
  .bg-gray-200 {
    background-color: #f0f0f0;
  }
  .bg-blue-200 {
    background-color: #e0f7fa;
  }
  .m-2 {
    margin: 8px;
  }
  .rounded {
    border-radius: 8px;
  }
  </style>
  