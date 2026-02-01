<script setup>
  import {ref} from 'vue';

  const title = ref ('Calceines VUE');
  const description = ref ('Par de calcetines VUE premium.')

</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ title }}</h1>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>