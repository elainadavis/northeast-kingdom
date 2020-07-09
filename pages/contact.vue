<template>
  <div class="gen-container">
    <h1>Contact Us</h1>
    <div class="contact-intro">
      <p v-html="contactData.intro"></p>
    </div>
  </div>
</template>
<script>
import contactData from 'static/hubdata/contact.json'

export default {
data: function(){
  return {
    contactData: contactData
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
