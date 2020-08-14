<template>
  <div  class="row">
    <form>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
        <label>Quote</label>
        <!-- 雙向綁定textarea and quote data -->
        <textarea class="form-control" name="" id="" rows="3" v-model="quote"></textarea>
      </div>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
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
      quote:''
    }
  },
  methods: {
    createNew(){
      // 產生事件，並將這邊輸入的quote回傳給，他這邊是先利用input with v-model更新到data，在創建事件做發射
      this.$emit('quoteAdded', this.quote)
      this.quote = ''
    }
  }
}
</script>

<style scoped>

</style>
