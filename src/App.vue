<template>
  <div id="app">
    <Home/>
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
</style>
