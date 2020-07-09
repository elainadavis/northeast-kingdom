<template>
  <div class="gen-container">
    <h1>Document Library</h1>
    <div class="library-intro">
      <p v-html="libraryData.intro"></p>
    </div>
  </div>
</template>
<script>
import libraryData from 'static/hubdata/library.json'

export default {
data: function(){
  return {
    libraryData: libraryData
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
