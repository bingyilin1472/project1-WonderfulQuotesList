<template>
  <div class="row">
    <div class="col-sm-12 title">
      <h3 class="header_title">Quotes Added</h3>
      <div class="progress">
        <!-- v-bind有特殊的寫法在class與style屬性上，style可以用obj方式讓多個樣式以key-value方式設定
             因為style屬性其中有許多sub-properties，並以Bootstrap with ARIA實踐進度條
         -->
        <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"
          :style="{width: (quoteCount / maxQuotes)*100 + '%'}">
          <!--  顯示在bar條上面的文字內容，因為bar是以div背景色和width來佔畫面，上面可以有內容 -->
          {{quoteCount}} / {{maxQuotes}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  // props屬性會綁定App.vue的data，更新最新狀態，顯示在進度條上(由parent元件輸入quote當前量與最大量)
  props: ['quoteCount', 'maxQuotes']
}
</script>

<style>
.header_title{
  margin-top: 10px;
  margin-bottom: 10px;
  font-family: sans-serif;
  font-weight: bold;
  font-size: 45px;
}
</style>
