<template>
  <div id="app" class="container">
    <img src="./assets/logo.png">
    <QuoteGrid :quotes="quotes"/>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
export default {
  name: 'App',
  data: function (){
    return{
      quotes:[
        'Just a Quote to see something',
        'Hello World',
        'Hello World',
        'Hello World',
        'Just a Quote to see something'
      ],
      maxQuotes: 10
    }
  },
  components: {
    QuoteGrid
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
  margin-top: 60px;
}
</style>
