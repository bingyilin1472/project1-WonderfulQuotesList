<template>
  <div id="app" class="container">
    <app-header :quote-count="quotes.length" :max-quotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
import NewQuote from "./components/NewQuote";
import Header from "./components/Header";
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
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },methods:{
    newQuote(quote){
      if (this.quotes.length >= this.maxQuotes){
        // 這部分比較特殊，因為alter是沒有回傳值，只會開啟跳窗
        // 等於他只是用return跳出func並且利用他執行一個expression
        return alert('Please delete Quotes first')
      }
      this.quotes.push(quote)
    },
    deleteQuote(index){
      // splice可以指定某位址並刪除指定數量
      this.quotes.splice(index,1);
    }
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
