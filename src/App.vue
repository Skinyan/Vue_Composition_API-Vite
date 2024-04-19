<template>
  <h1>{{ name }}</h1>
  <input type="text" v-model="name" />
  <button @click="placeOrder">Order</button>
  <button @click="removeWatcher">Hide Cart</button>
  <br /><br />
  <label for="currencySymbol">Currency</label>
  <select id="currencySymbol" v-model="currencySymbol">
    <option value="€">Euro (€)</option>
    <option value="$">Dollar ($)</option>
  </select>
  <YummyMeal
    v-for="meal in meals"
    :name="meal.name"
    :price="meal.price"
    @addToCart="addItemtToCart"
  />
</template>

<script setup>
import YummyMeal from "./components/YummyMeal.vue";
import { reactive, ref, watch, provide, onMounted } from "vue";

const currencySymbol = ref("€");
provide("currencySymbol", currencySymbol);
const name = ref("The Snazzy Burger");
const cart = reactive([]);
const meal = reactive({ name: "Hamburger", price: 5 });
const meals = reactive([
  {
    name: "Cheesburger",
    price: 5,
  },
  {
    name: "ChiliCheese",
    price: 5,
  },
  {
    name: "Impossible Burger",
    price: 800,
  },
  {
    name: "Fritten",
    price: 4,
  },
]);
const placeOrder = () => alert("your order is placed");
const addItemtToCart = (item) => cart.push(item);
const removeWatcher = watch([name, () => [...cart]], (newValue, oldValue) =>
  alert(newValue.join("\n"))
);

onMounted(() => {
  console.log(name.value);
});
</script>
