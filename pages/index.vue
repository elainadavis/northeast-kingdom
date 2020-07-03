<template>
  <div class="container">
    <div class="leading">
      <div class="imhold">
        <img src="~assets/images/client.jpg" />
      </div>
      <h1>TWISP Broadband Initiative</h1>
      <h3>Connecting Methow Valley to the 21st Century</h3>
      <p>
        Podunk unthaw owt Moody's robin showah noseeum gummah. Bangah junkah
        wreckah Bangoah some wicked, down east out in th' willie-wacks dooryahd,
        dingy hawsun around N'Hampshah gummah bookin' it aht mistah man. Nummah
        than a faht dinnahbucket hahd tellin' not knowin' whawf out in th'
        willie-wacks tunk what a cahd, wicked cunnin' bluebries Outta Staydahs
        up t' junkah buggin' yessah-bub leaf peepahs fellers, yow uns Powrtland
        Museum of Aht flatlandas heatah, stove up wickid decent owt junkah,
        scrod lobstah paut Jeesum Crow junkah moose Moxie Moosetown, aht whawf
        robin showah.
      </p>
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
export default {
  layout: "landing",
  data: function() {
    return {};
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
