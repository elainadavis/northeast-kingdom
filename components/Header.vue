<template>
  <div class="header">
    <a href="https://tilsonbbc.netlify.app/survey/" class="logo">
      <img src="~assets/images/twisp_survey_logo.jpg" width="250" height="52" />
    </a>
    <div class="header-right">
      <a class="active" href="https://tilsonbbc.netlify.app/">Home</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
/* Style for navbar on Survey page */
.header {
  overflow: hidden;
  background-color: #ffffff;
  padding: 10px 5px;
}

/* Header links */
.header a {
  float: left;
  color: black;
  text-align: center;
  padding: 8px;
  text-decoration: none;
  font-size: 18px;
  line-height: 25px;
  border-radius: 4px;
}

.header a.logo {
  font-size: 25px;
  font-weight: bold;
}

.header a:hover {
  background-color: #ddd;
  color: black;
}

/* Active/current link*/
.header a.active {
  background-color: #2aaee1;
  color: white;
}

.header-right {
  float: right;
  padding-right: 5px;
}

/* Media queries for responsiveness */
@media screen and (max-width: 500px) {
  .header a {
    float: none;
    display: block;
    text-align: left;
  }
  .header-right {
    float: none;
  }
}
</style>
