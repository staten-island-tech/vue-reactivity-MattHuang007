<script setup>
import { ref } from "vue";
import ItemButton from "./components/ItemButton.vue";
import { INGREDIENTS } from "./constants/ingredients";

const sandwichList = ref([]);
const ingredients = ref(INGREDIENTS);

function addIngredient(ingredient) {
  sandwichList.value.push(ingredient);
  window.scrollTo(
    0,
    document.body.scrollHeight || document.documentElement.scrollHeight
  );
}

function removeIngredient(index) {
  console.log(index);
  console.log(sandwichList.value[index]);
  sandwichList.value.splice(index, 1);
}
</script>

<template>
  <h1>Worlds Lowest Effort Sandwich Maker</h1>
  <h2>Click image to remove</h2>
  <header>
    <div v-for="ingredient in ingredients">
      <ItemButton :value="ingredient" @clicked="addIngredient(ingredient)" />
    </div>
  </header>

  <div
    v-for="(ingredient, index) in sandwichList"
    @click="removeIngredient(index)"
    class="horizontal-center"
  >
    <img :src="ingredient.src" class="ingredient" />
  </div>
  
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  background-color: gray;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.horizontal-center {
  display: flex;
  justify-content: center;
}
.ingredient {
  height: 100px;
  width: 100px;
 
}
</style>
