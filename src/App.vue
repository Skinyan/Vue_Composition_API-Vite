<template>
  <h1>{{ name }}</h1>
  <input type="text" v-model="name" />
  <button @click="placeOrder">ORdEr</button>
  <YummyMeal
    :name="meal.name"
    :price="meal.price"
    @addToCart="addItemtToCart"
  />
</template>

<script>
import YummyMeal from "./components/YummyMeal.vue";
import { reactive, ref } from "vue";

export default {
  components: { YummyMeal },
  setup() {
    const name = ref("The Snazzy Burger");
    const meal = reactive({ name: "Hamburger", price: 5 });
    const placeOrder = () => alert("your order is placed");
    const addItemtToCart = (item) => alert(`One ${item} added to the cart!`);

    return { name, placeOrder, addItemtToCart, meal };
  },
};
</script>
