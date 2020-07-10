<template>
  <div class="container">
    <div class="leading">
      <div class="imhold">
        <img src="~assets/images/client.jpg" />
      </div>
      <h1 v-html="generalData.projectName"></h1>
      <h3 v-html="generalData.projectByLine"></h3>
      <p v-html="generalData.landingText"></p>
    </div>
    <div class="site-sections">
      <a href="/library" class="ssection">
        <div class="iconholder">
          <img src="~assets/images/icons/library.svg" />
        </div>
        <h5>Document Library</h5>
      </a>
      <a href="/calendar" class="ssection">
        <div class="iconholder">
          <img src="~assets/images/icons/calendar.svg" />
        </div>
        <h5>Important Dates</h5>
      </a>
      <a href="/news" class="ssection">
        <div class="iconholder">
          <img src="~assets/images/icons/loudspeaker.svg" />
        </div>
        <h5>Recent News</h5>
      </a>
      <a href="/contact" class="ssection">
        <div class="iconholder">
          <img src="~assets/images/icons/community.svg" />
        </div>
        <h5>Contact Us</h5>
      </a>
      <a href="/survey" class="ssection">
        <div class="iconholder">
          <img src="~assets/images/icons/survey.svg" />
        </div>
        <h5>Community Survey</h5>
      </a>
    </div>
  </div>
</template>

<script>
import generalData from "static/hubdata/general.json";

export default {
  layout: "landing",
  data: function() {
    return {
      generalData: generalData
    };
  },
  methods: {}
};
</script>

<style lang="scss">
.leading {
  text-align: center;
  max-width: 900px;
  padding: 20px;
  margin: 0 auto;
  p {
    text-align: left;
  }
  .imhold {
    font-size: 30px;
    font-weight: 900;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
    img {
      width: 120px;
      margin: 20px;
    }
  }
}
.site-sections {
  display: flex;
  max-width: 1000px;
  margin: 0 auto;
  flex-wrap: wrap;
  justify-content: center;
  position: relative;
  .ssection {
    width: 20%;
    max-width: 140px;
    padding: 20px;
    text-decoration: none;
    color: #000;
    display: flex;
    flex-direction: column;
    align-items: center;
    &:hover,
    &:focus {
      outline: none;
      .iconholder {
        border: 3px solid #2aaee1;
        border-radius: 50%;
        transition: all 0.2s ease-in-out;
        background-color: #2aade13f;
        img {
          transform: scale(0.75);
          transition: all 0.2s ease-in-out;
        }
      }
      h5 {
        color: #2aaee1;
        transition: all 0.2s ease-in-out;
      }
    }
    .iconholder {
      border: 3px solid transparent;
      border-radius: 50%;
      transition: all 0.2s ease-in-out;
      width: 100%;
      img {
        width: 100%;
        transition: all 0.2s ease-in-out;
      }
    }
    h5 {
      font-size: 16px;
      font-weight: bold;
      padding-top: 20px;
      text-align: center;
      transition: all 0.2s ease-in-out;
    }
  }
}
</style>
