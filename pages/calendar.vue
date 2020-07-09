<template>
  <div class="gen-container">
    <h1>Important Dates</h1>
    <div class="calendar-intro">
      <p v-html="calendarData.intro"></p>
    </div>
  </div>
</template>
<script>
import calendarData from 'static/hubdata/calendar.json'

export default {
data: function(){
  return {
    calendarData: calendarData
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
