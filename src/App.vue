<template>
  <div id="app" class="container">
    <app-header :quote-count="quotes.length" :max-quotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div v-if="notice.length != 0" class="alert alert-info">Notice: {{notice}}</div>
        <div class="alert alert-info" v-if="quotes.length==10">Notice: Click on a Quote to delete it!</div>
      </div>
    </div>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
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
        'Albert Einstein: Logic will get you from A to B. Imagination will take you everywhere.',
        'A man is not old as long as he is seeking something. A man is not old until regrets take the place of dreams.',
      ],
      maxQuotes: 10,
      notice: ""
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },methods:{
    newQuote(quote){
      // if (this.quotes.length >= this.maxQuotes){
      //   // 這部分比較特殊，因為alter是沒有回傳值，只會開啟跳窗
      //   // 等於他只是用return跳出func並且利用他執行一個expression
      //   return this.notice = 'Please delete Quotes first'
      // }
      if (this.quotes.length < this.maxQuotes){
        if(quote.length!=0){
          this.notice = ""
          this.quotes.push(quote)
        }else{
          // 這部分比較特殊，因為alter是沒有回傳值，只會開啟跳窗
          // 等於他只是用return跳出func並且利用他執行一個expression
          this.notice = "Please enter some content for your quote."
        }
      }
    },
    deleteQuote(index){
      // splice可以指定某位址並刪除指定數量
      this.quotes.splice(index,1);
    }
  }
}
</script>

<style>
#app{
  text-align: left;
}
</style>
