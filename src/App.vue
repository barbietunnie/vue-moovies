<template>
  <div id="app">
    <Header title="Movies DB" />
    <router-view />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import MoviesList from './components/MoviesList.vue';

export default {
  name: 'app',
  data() {
    return {
      name: 'Scott'
    }
  },
  computed: {
    
  },
  components: {
    Header,
    MoviesList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
