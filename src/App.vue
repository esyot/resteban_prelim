<script setup>
import FilteredItems from './components/filteredItems.vue';
import Items from './components/Items.vue'
</script>

<template>
<div class="flex items-center justify-center"> 
  <div id="container" class="flex">

  </div>
  <div class="flex flex-col bg-gray-200 p-2">
    <h1>
      Items List:
    </h1>
  <Items/>
  </div>

  <div>
    <h1>Filtered Items:</h1>

  <FilteredItems/>

  </div>

  

  </div>

</template>

