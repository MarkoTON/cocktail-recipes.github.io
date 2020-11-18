<template>
  <div v-scroll="handleScroll" id="top-list" class="home container pt-3 ">
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
          </div><!-- card-body text-white text-shadow -->
        </div><!-- col-md-8 -->
      </div>
    </div><!-- card mb-3  -->
    <!-- <a href="#top-list" class="btn-to-top">
      <i class="fa fa-arrow-up fa-lg"></i>
    </a> -->

  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash/debounce';

export default {
  name: 'Home',
  data () {
    return {
      info:null,
      slide: 0,
      sliding: null
    }
  },
  methods: {
    handleScroll (event) {
      // Any code to be executed when the window is scrolled
      // console.log(event)
      // console.log("metallica")
      this.isUserScrolling = (window.scrollY > 0);
      console.log(this.isUserScrolling);
      console.log('calling handleScroll');
    },
    onSlideStart(slide) {
      this.sliding = true
    },
    onSlideEnd(slide) {
      this.sliding = false
    }
  },
  created() {
    this.handleDebouncedScroll = debounce(this.handleScroll, 0);
    window.addEventListener('scroll', this.handleDebouncedScroll);
  },
  beforeDestroy() {
    // I switched the example from `destroyed` to `beforeDestroy`
    // to exercise your mind a bit. This lifecycle method works too.
    window.removeEventListener('scroll', this.handleDebouncedScroll);
  },
  destroyed () {
    this.list.removeEventListener('scroll', this.handleScroll);
  },
  mounted () {
    axios
      .get('https://www.thecocktaildb.com/api/json/v1/1/search.php?f=a')
      .then(response => (this.info = response.data.drinks));
    this.list = document.getElementById('top-list')
    this.list.addEventListener('scroll', this.handleScroll);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.text-shadow {
  text-shadow: 1px 1px 1px rgba(0,0,0,0.8);
}

#top-list {
  height:100%;
  overflow: auto;
}

#top-list::-webkit-scrollbar{
  width:8px;
}

#top-list::-webkit-scrollbar-track {
  background: #ddd;
}

#top-list::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255,0.3);
}

#top-list::-webkit-scrollbar-track{
  background: rgba(0, 0, 0, 0.1);
}

.btn-to-top {
	border-radius: 50%;
  border:2px solid rgba(15, 15, 105, 0.87);
  background: rgba(255, 255, 255, 0.5);
  text-align: center;
  line-height: 42px;
  height: 50px;
  width: 50px;
  font-size: 20px;
	opacity: 0.5;
	position: fixed;
  right: 50%;
  bottom: 10px;
	cursor: pointer;
	-webkit-transition: all .3s ease;
  -moz-transition: all .3s ease;
  -o-transition: all .3s ease;
  -ms-transition: all .3s ease;
  transition: all .3s ease;
  display: none;
}
.btn-to-top:hover {
	opacity: 1;
}
</style>
