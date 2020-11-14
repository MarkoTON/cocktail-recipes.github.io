<template>
  <div class="home container pt-3 ">
    <div class="card mb-3 " style="background:rgba(0,0,0,0.5)" v-for="(item,index) in info" :key="index">
      <div class="row no-gutters">
        <div class="col-md-4">
          <img style="height:100%" :src="item.strDrinkThumb" class="card-img" alt="...">
        </div>
        <div class="col-md-8">
          <div class="card-body text-white text-shadow">
            <h5 class="card-title ">{{item.strDrink}}</h5>
            <p class="card-text ">{{item.strInstructions}}</p>
            <p>Ingredients:</p>
            <ul>
              <li v-if="item.strIngredient1">{{item.strIngredient1}} : {{ item.strMeasure1 }}</li>
              <li v-if="item.strIngredient2">{{item.strIngredient2}} : {{ item.strMeasure2 }}</li>
              <li v-if="item.strIngredient3">{{item.strIngredient3}} : {{ item.strMeasure3 }}</li>
              <li v-if="item.strIngredient4">{{item.strIngredient4}} : {{ item.strMeasure4 }}</li>
              <li v-if="item.strIngredient5">{{item.strIngredient5}} : {{ item.strMeasure5 }}</li>
              <li v-if="item.strIngredient6">{{item.strIngredient6}} : {{ item.strMeasure6 }}</li>
              <li v-if="item.strIngredient7">{{item.strIngredient7}} : {{ item.strMeasure7 }}</li>
              <li v-if="item.strIngredient8">{{item.strIngredient8}} : {{ item.strMeasure8 }}</li>
              <li v-if="item.strIngredient9">{{item.strIngredient9}} : {{ item.strMeasure9 }}</li>
              <li v-if="item.strIngredient10">{{item.strIngredient10}} : {{ item.strMeasure10 }}</li>
              <li v-if="item.strIngredient11">{{item.strIngredient11}} : {{ item.strMeasure11 }}</li>
              <li v-if="item.strIngredient12">{{item.strIngredient12}} : {{ item.strMeasure12 }}</li>
              <li v-if="item.strIngredient13">{{item.strIngredient13}} : {{ item.strMeasure13 }}</li>
              <li v-if="item.strIngredient14">{{item.strIngredient14}} : {{ item.strMeasure14 }}</li>
              <li v-if="item.strIngredient15">{{item.strIngredient15}} : {{ item.strMeasure15 }}</li>
            </ul>
            <p>Glass: {{ item.strGlass }}</p>
            <p>Category: {{ item.strCategory }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data () {
    return {
      info:null
    }
  },
  methods: {
    
  },
  mounted () {
    axios
      .get('https://www.thecocktaildb.com/api/json/v1/1/search.php?f=a')
      .then(response => (this.info = response.data.drinks));
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.text-shadow {
  text-shadow: 1px 1px 1px rgba(0,0,0,0.8);
}
</style>
