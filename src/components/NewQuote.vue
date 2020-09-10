<template>
  <div class="row">
    <form class="quote-form">
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
        <label class="input_title" name="quote-input">Quote</label>
        <!-- 雙向綁定textarea and quote data -->
        <textarea class="form-control" name="quote-input" rows="3" v-model="quote"></textarea>
      </div>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group2">
        <!-- prevent modifier防止default submit去server to reload page -->
        <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "NewQuote",
  data: function (){
    return{
      quote: ""
    }
  },
  methods: {
    createNew(){
      if(this.quote.length == 0){
        // if或else都是
        this.$emit('quoteAdded', this.quote)
      }else {
        // 產生事件，並將這邊輸入的quote回傳給，他這邊是先利用input with v-model更新到data，在創建事件做發射
        this.$emit('quoteAdded', this.quote)
        this.quote = ""
      }
    }
  }
}
</script>

<style>
  .input_title{
    margin-top: 5px;
    font-family: sans-serif;
    font-weight: bold;
    font-size: 25px;
  }
  .quote-form{
    display: inline-block;
    text-align: center;
    width: 100%;
  }
  .form-group{
    text-align: left;
    display: inline-block;
  }
  .form-group2{
    text-align: left;
    display: inline-block;
    margin-bottom: 10px;
  }
</style>
