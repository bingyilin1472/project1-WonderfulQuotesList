<template>
  <div class="row">
    <div class="col-sm-12">
      <h3>Quotes Added</h3>
      <div class="progress">
        <!-- v-bind有特殊的寫法在class與style屬性上，style可以用obj方式讓多個樣式以key-value方式設定  -->
        <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"
          :style="{width: (quoteCount / maxQuotes)*100 + '%'}">
          <!--  顯示在bar條上面的文字內容 -->
          {{quoteCount}} / {{maxQuotes}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  // props屬性會綁定App.vue的data，更新最新狀態，顯示在進度條上
  props: ['quoteCount', 'maxQuotes']
}
</script>

<style scoped>

</style>
