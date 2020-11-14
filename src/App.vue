<template>
  <div id="app">
    <Home/>
    <div title="Back to top" class="btn btn-primary btn-to-top">
      <i class="fas fa-arrow-circle-up"></i>
    </div>
  </div>
</template>

<script>
import Home from './components/Home'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
#app {
  background: url('./assets/bg-image-cocktail.jpg');
  background-position: center center;
  background-size: cover;
  height: 100vh;
  overflow: auto;
}

#app::-webkit-scrollbar{
  width:8px;
}

#app::-webkit-scrollbar-track {
  background: #ddd;
}

#app::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255,0.3);
}

#app::-webkit-scrollbar-track{
  background: rgba(0, 0, 0, 0.1);
}

.btn-to-top {
	border-radius: 50%;
    text-align: center;
    line-height: 34px;
    height: 50px;
    width: 50px;
    font-size: 20px;
	opacity: 0.5;
	position: fixed;
    right: 10px;
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
