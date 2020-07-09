<template>
  <div class="gen-container">
    <h1>Recent News</h1>
    <div class="news-intro">
      <p v-html="newsData.intro"></p>
    </div>
  </div>
</template>
<script>
import newsData from 'static/hubdata/news.json'

export default {
data: function(){
  return {
    newsData: newsData
  }
}
};
</script>
<style lang="scss" scoped>
.gen-container {
  padding: 80px 15px;
  max-width: 900px;
  margin: 0 auto;
  h1{
    text-align: center;
  }
}
</style>
