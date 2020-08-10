<template>
  <div class="row">
      <Quote v-for="quote in quotes">{{ quote }}</Quote>
  </div>
</template>

<script>
import Quote from "./Quote";
export default {
  name: "QuoteGrid",
  // 自訂一properties，可以讓你從parent注入時候定義屬性帶data到此template/component之中
  props: ['quotes'],
  data: function (){
    return{
      name: 'Dante',
      info: 'test'
    }
  },
  components:{
    Quote
  }
}
</script>

<style>
</style>
