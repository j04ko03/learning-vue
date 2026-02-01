<script setup>
import { ref } from 'vue'
import imagenCalcetinVerde from './assets/images/socks_green.jpeg'
import imagenCalcetinAzul from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const imagen = ref(imagenCalcetinVerde)
const url = ref ('https://www.vuemastery.com/courses/intro-to-vue-3-comp-api/introduction-comp-api')


</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="imagen" alt="Calcetinez verdes VUE.">
        <a :href="url">Ver más info</a>
        <!-- image goes here -->
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
      </div>
    </div>
  </div>
</template>