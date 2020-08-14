<template>
  <div class="row">
      <!-- native modifier可以去抓他其中的native element是否有click的event(也可搭配其他event)
           若監測到其中的原生element有，就將index傳回，v-for可以取內容以及它的位置index索引
         -->
      <Quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">{{ quote }}</Quote>
  </div>
</template>

<script>
import Quote from "./Quote";
export default {
  name: "QuoteGrid",
  // 自訂一properties，可以讓你從parent注入時候定義屬性帶data到此template/component之中
  // 綁定parent的quotes，正因為此index才回一致，傳回才能刪除對的
  props: ['quotes'],
  data: function (){
    return{
      name: 'Dante',
      info: 'test'
    }
  },
  components:{
    Quote
  },
  methods:{
    deleteQuote(index){
      // 將component的method作為一個事件發送出去(custom event)
      // 這樣就能將component的一些結果帶出去給他的parent component or root
      this.$emit("quoteDeleted", index)
    }
  }
}
</script>

<style>
</style>
