<template>
  <div
    class="shadow-2xl max-w-sm px-5 py-4 rounded bg-white"
   
  >
    <div class="flex">
      <div class="flex h-28 w-28 overflow-hidden rounded shadow-xl">
        <img class="object-fit" :src="meal.strMealThumb" alt="" />
      </div>
      <div class="ml-2 flex-1 flex flex-col">
          <h1 class="text-xl font-bold">{{ meal.strMeal }}</h1>
          <div  class="my-2 w-auto rounded text-gray-500">{{ meal.strCategory }}</div>
      </div>
    </div>
    <div>
      <h1 class="text-xl font-bold mt-2">Ingredients</h1>
      <div class="flex flex-wrap">
        <div
          v-for="(obj, index) in ingredient"
          :key="index"
          class="bg-purple-500 px-3 py-2 my-2 mx-2 rounded text-white shadow-xl"
        >
          {{ obj }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    meal: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      ingredients: [],
      categories:{
        'Beef': 'bg-yellow-700',
        'Chicken': 'bg-red-200',
        'Dessert': 'bg-yellow-900',
        'Lamb': 'bg-red-200',
        'Miscellaneous': 'bg-red-200',
        'Pasta': 'bg-red-200',
        'Pork': 'bg-red-200',
        'Seafood': 'bg-green-600',
        'Side': 'bg-red-200',
        'Vegan': 'bg-red-200',
        'Vegetarian': 'bg-red-200',
        'Breakfast': 'bg-red-200',
        'Goat': 'bg-red-500',
      },
      }
    },
  computed: {
    ingredient: function () {
      for (let obj in this.meal) {
        if (obj.includes("strIngredient")) {
          if (this.meal[obj] != null && this.meal[obj] != "") {
            this.ingredients.push(this.meal[obj]);
          }
        }
      }
      return this.ingredients;
    },
  },

  //  :class=" categories.hasOwnProperty(meal.strCategory) ?  categories[ meal.strCategory] : 'bg-white'"
}
</script>

<style></style>
