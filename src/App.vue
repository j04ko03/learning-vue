<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
// const disp = ref(true)
const inv = ref(5)
const enVenta = ref(true)

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="enVenta">Disponible</p>
        <!-- <p v-show="disp">Disponible</p> -->
        <p v-else-if="inv <= 10 && inv > 0">Casi sin existencia</p>
        <p v-else>No disponible</p>
      </div>
    </div>
  </div>
</template>