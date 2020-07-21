<template>
  <div class="container">
    <div class="form-container" id="speedcheckcontainer">
      <div class="introtitle">
        <h1>Community Survey</h1>
        <h3 v-html="surveyData.intro"></h3>
      </div>
      <div id="addressLookupContainer">
        <div class="formg">
          <label for="address_input">Street Address:</label>
          <input type="text" id="address_input" name="address_input" v-model="user_address" />
        </div>
        <div class="formg">
          <label for="zipcode_input">Zipcode:</label>
          <input type="text" id="zipcode_input" name="zipcode_input" v-model="user_zip" />
        </div>
        <button class="lookupbutt" v-on:click="getGeocodioInfo()">Lookup Address</button>
        <div
          class="address_error_message"
          v-bind:class="{ visible: address_error }"
        >{{address_error}}</div>
        <div class="addressLookupBox" v-bind:class="{ visible: geoLookupResults.length }">
          <h4>Please Select Your Verified Address, you will then be prompted to run a speed test to check your internet connection:</h4>
          <ul class="addresslookup" v-for="result in geoLookupResults" v-bind:key="result">
            <li v-on:click="addressVerified(result)" v-html="result.formatted_address"></li>
          </ul>
        </div>
      </div>
      <div id="sc-container" style="display: none;">
        <div id="sc-branding" class="sc-bb">
          <a target="_blank" href="https://www.speedcheck.org/">
            <img src="https://cdn.speedcheck.org/branding/speedcheck-logo-18.png" alt="Speedcheck" />
          </a>
        </div>
      </div>
    </div>
    <script src="https://cdn.speedcheck.org/basic/scbjs.min.js" async></script>
    <div id="survey-panel" class="panel panel-white panel-no-border hide">
      <div id="survey123-webform" class="panel panel-no-padding panel-no-border"></div>
    </div>
  </div>
</template>

<script>
import surveyData from "static/hubdata/survey.json";

export default {
  mounted: function() {
    let vm = this;
    var open = window.XMLHttpRequest.prototype.open,
      send = window.XMLHttpRequest.prototype.send;

    function openReplacement(method, url, async, user, password) {
      this._url = url;
      return open.apply(this, arguments);
    }

    function sendReplacement(data) {
      /**
       * PLACE HERE YOUR CODE WHEN REQUEST IS SENT
       */
      if (this._url == "https://api.speedspot.org/basic" && arguments[0]) {
        console.log(arguments[0]);
        vm.results = JSON.parse(arguments[0]);
        if (!vm.formInitialized) {
          vm.initializeForm(vm.results);
        }
      }
      return send.apply(this, arguments);
    }

    window.XMLHttpRequest.prototype.open = openReplacement;
    window.XMLHttpRequest.prototype.send = sendReplacement;
  },
  data: function() {
    return {
      results: {},
      formInitialized: false,
      surveyData: surveyData,
      user_address: "",
      user_zip: "",
      geoLookupResults: [],
      verified_address: {},
      address_error: null
    };
  },
  methods: {
    getGeocodioInfo: function() {
      let vm = this;
      vm.address_error = null;
      if (!vm.user_address || !vm.user_zip) {
        vm.address_error =
          "Incomplete information, please enter your street address and zipcode and try again.";
      } else {
        this.$axios
          .get(
            `https://api.geocod.io/v1.6/geocode?q=${vm.user_address},${vm.user_zip}&api_key=a01b3ce373bbbb3fba37e7c05af0ef52fff05fc`
          )
          .then(function(response) {
            if (
              response.data.results === undefined ||
              response.data.results.length == 0
            ) {
              vm.address_error =
                "Unfortunately we weren't able to find results for that address/zipcode.  Please ensure your information is entered correctly.";
            }
            vm.geoLookupResults = response.data.results;
            console.log(response);
          })
          .catch(function(error) {
            vm.address_error = error.message;
            console.log(error);
          });
      }
    },
    addressVerified: function(verifiedResultObj) {
      let vm = this;
      vm.verified_address = verifiedResultObj;
      document.getElementById("addressLookupContainer").style.display = "none";
      document.getElementById("sc-container").style.display = "block";
    },
    initializeForm: function(speedData) {
      let vm = this;
      this.formInitialized = true;
      document.getElementById("speedcheckcontainer").style.display = "none";
      const survey123WebForm = new Survey123WebForm({
        container: "survey123-webform",
        clientId: vm.surveyData.clientId,
        portalUrl: "https://www.arcgis.com",
        itemId: vm.surveyData.itemId,
        hideElements: "navbar",
        onFormLoaded: data => {
          //
          // ANSWER INTERNET SPEED QUESTION WITH CONNECTION SPEED INFO //
          //
          survey123WebForm.setQuestionValue({
            download_speed: speedData.downloadValue,
            upload_speed: speedData.uploadValue,
            latency: speedData.pingValue,
            internet_browser: speedData.browser.browser,
            operating_sys: speedData.browser.os,
            full_address: vm.verified_address.formatted_address,
            user_lat: vm.verified_address.location.lat,
            user_long: vm.verified_address.location.lng,
            user_device: speedData.browser.device,
            user_isp: speedData.isp.isp,
            isp_lat: speedData.isp.lat,
            isp_long: speedData.isp.lon,
          });
        }
      });
      // SHOW SURVEY123 FORM //
      let surveyPanel = document.getElementById("survey-panel");
      surveyPanel.classList.remove("hide");
    }
  }
};
</script>

<style lang="scss">
.lookupbutt {
  padding: 17px 30px;
  border-radius: 50px;
  border: none;
  background-color: #2aaee1;
  color: #fff;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin: 20px 0;
  cursor: pointer;
}
#addressLookupContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .formg {
    margin: 10px;
    width: 310px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    label {
      padding-right: 10px;
    }
  }
}
.addressLookupBox {
  display: none;
  h4 {
    color: #2aaee1;
  }
  ul {
    padding: 0;
  }
  &.visible {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
.addresslookup {
  li {
    padding: 10px;
    cursor: pointer;
    list-style-type: none;
    margin: 0;
    padding: 10px 28px;
    margin: 10px 0;
    &:hover {
      background-color: #c4f4ff;
      color: #000;
      border-radius: 50px;
      box-shadow: 0 2px 1px #b6b6b6;
    }
  }
}
.address_error_message {
  display: none;
  color: #e95331;
  &.visible {
    display: block;
  }
}
#speedcheckcontainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 180px);
  .introtitle {
    max-width: 900px;
    text-align: center;
    margin: 15px;
    color: #2aaee1;
    padding-bottom: 30px;
  }
}
.iframecontainer {
  margin: 40px;
  background-color: rgb(26, 26, 26);
}
.form-container {
  display: flex;
  justify-content: center;
  align-items: center;
  #sc-container {
    .sc-bb {
      display: none;
    }
    .sc-button {
      cursor: pointer;
    }
    #sc-basic-link {
      display: none;
    }
    #sc-footer {
      display: none;
    }
  }
}
.column {
  float: left;
  padding: 10px;
}
.address-box {
  display: block;
  margin: 0 auto;
  height: 30px;
  width: 75%;
  font-family: "Roboto", sans-serif;
  font-size: 20px;
}

@media only screen and (max-width: 700px) {
}
</style>
