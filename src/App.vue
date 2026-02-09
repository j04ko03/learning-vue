<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const brand = ref('Vue Mastery')
const onSale = ref(true)

const selectedVariant = ref(0)
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50, price: 10 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 10, price: 12 },
])

const cart = ref([])

const addToCart = () => cart.value.push(variants.value[selectedVariant.value])

const removeFromCart = () => {
  const itemToRemove = variants.value[selectedVariant.value]
  const index = cart.value.indexOf(itemToRemove)
  if (index > -1) {
    cart.value.splice(index, 1)
  }
}

const totalItems = computed(() => cart.value.length)

const totalCost = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0))

const updateVariant = (index) => {
  selectedVariant.value = index
  console.log(index)
}

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const title = computed(() => {
  if (onSale.value ) {
    return brand.value + ' ' + product.value + ' is on sale'
  }
  return brand.value + ' ' + product.value
})

const image = computed (() => {
  return variants.value [selectedVariant.value].image
})

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ totalItems }}) Total: {{ totalCost }}€</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ title }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div 
          v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        >
        </div>
        <button
          class="button" 
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
        <button 
          class="button" 
          @click="removeFromCart"
        >
          Remove Item
        </button>
      </div>
    </div>
  </div>
</template>