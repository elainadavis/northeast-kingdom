<template>
  <div class="container">
    <div class="leading">
      <div class="imhold">
        <img src="~assets/images/client.jpg" />
        +
        <img src="~assets/images/tilson.png" />
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
      <a href="/survey.html" class="ssection">
        <img src="~assets/images/icons/library.svg" />
        <h5>Document Library</h5>
      </a>
      <a href="/survey.html" class="ssection">
        <img src="~assets/images/icons/calendar.svg" />
        <h5>Important Dates</h5>
      </a>
      <a href="/survey.html" class="ssection">
        <img src="~assets/images/icons/loudspeaker.svg" />
        <h5>Recent News</h5>
      </a>
      <a href="/survey.html" class="ssection">
        <img src="~assets/images/icons/community.svg" />
        <h5>Contact Us</h5>
      </a>
      <a href="/survey.html" class="ssection">
        <img src="~assets/images/icons/survey.svg" />
        <h5>Community Survey</h5>
      </a>
    </div>
  </div>
</template>

<script>
export default {
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
  padding: 50px 20px 20px 20px;
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
      width: 80px;
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
    width: 25%;
    max-width: 160px;
    padding: 20px;
    text-decoration: none;
    color: #000;
    img {
      width: 100%;
    }
    h5 {
    }
  }
}
</style>
