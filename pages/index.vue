<template>
  <div class="bg-gray-800 flex flex-col items-center">
    <div class="text-4xl text-center text-gray-900 my-8 bg-white px-8 py-4 rounded">
     Random Meals
    </div>
    <div class="grid grid-cols-3 gap-5">
      <Meal v-for="(meal,index) in meals" :key="index" :meal="meal" />
    </div>
  </div>
</template>

<script>
export default {

  data(){
    return {
      meals: [],
      ingredients: [],
    }
  },
 async  mounted() {

   for (var i = 0; i <10; i++ ){
     const recipe = (await this.$axios.get("https://www.themealdb.com/api/json/v1/1/random.php")).data
      this.meals.push(recipe.meals[0])
   }
  },
  methods:{
    

  }
}
</script>
