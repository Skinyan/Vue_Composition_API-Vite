<template>
  <p>
    <strong>{{ name }}:</strong>
    <YummyMealPrice :price="price" />
    <button @click="addToCart">Add to Cart</button>
  </p>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps({
  name: String,
  price: Number,
});

const emit = defineEmits(["addToCart"]);

import YummyMealPrice from "./>YummyMealPrice.vue";
const addToCart = () => emit("addToCart", props.name);
</script>
