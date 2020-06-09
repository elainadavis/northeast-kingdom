<template>
  <div class="container">
    <div class="leading">
      <h1>
        TWISP Broadband Initiative
      </h1>
      <h4>
        Connecting Methow Valley to the 21st Century
      </h4>
      <div class="form-container">
        <div id="sc-container">
          <div id="sc-branding" class="sc-bb">
            <a target="_blank" href="https://www.speedcheck.org/">
              <img
                src="https://cdn.speedcheck.org/branding/speedcheck-logo-18.png"
                alt="Speedcheck"
              />
            </a>
          </div>
        </div>
      </div>
      <script
        src="https://cdn.speedcheck.org/basic/scbjs.min.js"
        async
      ></script>
      <div>
        <pre v-if="results">{{ results }}</pre>
      </div>
      <!-- <div class="iframecontainer"> -->
      <!-- <iframe width="100%" height="650px" frameborder="0" src="https://tilson.speedtestcustom.com"></iframe> -->
      <!-- </div> -->
    </div>
  </div>
</template>

<script>
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
      }
      return send.apply(this, arguments);
    }

    window.XMLHttpRequest.prototype.open = openReplacement;
    window.XMLHttpRequest.prototype.send = sendReplacement;
  },
  data: function() {
    return {
      uploadSpeed: null,
      downloadSpeed: null,
      results: {}
    };
  }
};
</script>

<style lang="scss">
.leading {
  text-align: center;
  margin-top: 50px;
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
</style>
