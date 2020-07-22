<template>
  <div class="header">
    <div class="header-left">
      <a href="/" class="logo">
        <img src="~assets/images/client.jpg" />
      </a>
      {{generalData.projectName}}
    </div>
    <div class="mobilham" @click="openMenu()">
      <svg
        height="100px"
        width="100px"
        fill="#000000"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        viewBox="0 0 64 64"
        version="1.1"
        xml:space="preserve"
        style
        x="0px"
        y="0px"
        fill-rule="evenodd"
        clip-rule="evenodd"
        stroke-linejoin="round"
        stroke-miterlimit="1.41421"
      >
        <rect x="0" y="0" width="64" height="64" style fill="none" />
        <path
          d="M46.127,21.505c0.112,0.015 0.141,0.015 0.251,0.043c0.288,0.075 0.551,0.237 0.748,0.461c0.112,0.128 0.203,0.274 0.266,0.432c0.063,0.157 0.099,0.326 0.107,0.495c0.023,0.561 -0.278,1.1 -0.767,1.374c-0.149,0.082 -0.311,0.14 -0.478,0.168c-0.112,0.02 -0.141,0.017 -0.254,0.022l-28,0c-0.113,-0.005 -0.142,-0.002 -0.253,-0.022c-0.294,-0.05 -0.57,-0.189 -0.785,-0.395c-0.123,-0.118 -0.225,-0.256 -0.301,-0.408c-0.077,-0.151 -0.127,-0.316 -0.149,-0.484c-0.06,-0.468 0.11,-0.948 0.45,-1.274c0.092,-0.088 0.195,-0.164 0.306,-0.227c0.149,-0.082 0.311,-0.14 0.479,-0.168c0.111,-0.02 0.14,-0.017 0.253,-0.022l28,0c0.042,0.002 0.085,0.004 0.127,0.005Z"
          style
          fill-rule="nonzero"
        />
        <path
          d="M46.127,30.505c0.112,0.015 0.141,0.015 0.251,0.043c0.288,0.075 0.551,0.237 0.748,0.461c0.112,0.128 0.203,0.274 0.266,0.432c0.209,0.52 0.104,1.129 -0.266,1.55c-0.112,0.128 -0.246,0.236 -0.394,0.319c-0.149,0.082 -0.311,0.14 -0.478,0.168c-0.112,0.02 -0.141,0.017 -0.254,0.022l-28,0c-0.113,-0.005 -0.142,-0.002 -0.253,-0.022c-0.168,-0.028 -0.33,-0.086 -0.479,-0.168c-0.411,-0.231 -0.696,-0.652 -0.756,-1.119c-0.016,-0.127 -0.016,-0.255 0,-0.382c0.022,-0.168 0.072,-0.333 0.149,-0.484c0.076,-0.152 0.178,-0.29 0.301,-0.408c0.215,-0.206 0.491,-0.345 0.785,-0.395c0.111,-0.02 0.14,-0.017 0.253,-0.022l28,0c0.042,0.002 0.085,0.004 0.127,0.005Z"
          style
          fill-rule="nonzero"
        />
        <path
          d="M46.127,39.505c0.112,0.015 0.141,0.015 0.251,0.043c0.288,0.075 0.551,0.237 0.748,0.461c0.37,0.421 0.475,1.03 0.266,1.55c-0.063,0.158 -0.154,0.304 -0.266,0.432c-0.112,0.128 -0.246,0.236 -0.394,0.319c-0.149,0.082 -0.311,0.14 -0.478,0.168c-0.112,0.02 -0.141,0.017 -0.254,0.022l-28,0c-0.113,-0.005 -0.142,-0.002 -0.253,-0.022c-0.294,-0.05 -0.57,-0.189 -0.785,-0.395c-0.092,-0.088 -0.172,-0.188 -0.239,-0.297c-0.248,-0.401 -0.291,-0.908 -0.115,-1.345c0.064,-0.158 0.154,-0.304 0.266,-0.432c0.112,-0.128 0.246,-0.236 0.394,-0.319c0.149,-0.082 0.311,-0.14 0.479,-0.168c0.111,-0.02 0.14,-0.017 0.253,-0.022l28,0c0.042,0.002 0.085,0.004 0.127,0.005Z"
          style
          fill-rule="nonzero"
        />
      </svg>
    </div>
    <div class="header-right menuClosed">
      <div class="xout" @click="closeMenu()">
        <svg
          height="100px"
          width="100px"
          fill="#000000"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          xml:space="preserve"
          version="1.1"
          style="shape-rendering:geometricPrecision;text-rendering:geometricPrecision;image-rendering:optimizeQuality;"
          viewBox="0 0 847 847"
          x="0px"
          y="0px"
          fill-rule="evenodd"
          clip-rule="evenodd"
        >
          <defs>
            <style type="text/css">
  .fil0 {
    fill: #ffffff;
  }
            </style>
          </defs>
          <g>
            <path
              class="fil0"
              d="M423 530l-273 273c-70,70 -176,-37 -106,-107l273 -273 -273 -273c-70,-70 36,-176 106,-106l273 273 273 -273c70,-70 177,36 107,106l-273 273 273 273c70,70 -37,177 -107,107l-273 -273z"
            />
          </g>
        </svg>
      </div>
      <nuxt-link
        v-for="page in pages"
        v-bind:key="page.name"
        v-html="page.name"
        :to="`/${page.slug}`"
      ></nuxt-link>
    </div>
  </div>
</template>
<script>
import generalData from "static/hubdata/general.json";

export default {
  data: function() {
    return {
      generalData: generalData,
      pages: [
      ]
    };
  },
  watch: {
    $route() {
      this.closeMenu();
    }
  },
  methods: {
    closeMenu: function() {
      document.querySelector(".header-right").classList.add("menuClosed");
    },
    openMenu: function() {
      document.querySelector(".header-right").classList.remove("menuClosed");
    }
  }
};
</script>
<style lang="scss" scoped>
/* Style for navbar on Survey page */
.header {
  overflow: hidden;
  background-color: #ffffff;
  height: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  box-shadow: 0 2px 5px 2px #b3b3b3;
  .mobilham {
    display: none;
  }
}

.header a.logo img {
  height: 60px;
  margin-right: 15px;
}

.header a:hover {
  // background-color: #ddd;
  // color: black;
}

.header-left {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 25px;
  font-family: "Fjalla One", sans-serif;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.header-right {
  transition: 0.2s ease-in-out;
  .xout {
    display: none;
  }
  a {
    font-size: 14px;
    font-weight: 800;
    float: left;
    color: black;
    text-align: center;
    padding: 8px 15px;
    text-decoration: none;
    border-radius: 50px;
    &.active-nav-link {
      color: #2aaee1;
    }
    &:hover {
      background: #2aaee1;
      color: #fff;
    }
  }
}

@media only screen and (max-width: 1080px) {
  .header {
    .mobilham {
      display: block;
      cursor: pointer;
      svg {
        height: 50px;
      }
    }
    .header-right {
      display: flex;
      flex-direction: column;
      position: absolute;
      background: #2aaee1;
      right: 0;
      top: 0;
      padding: 0px;
      width: 280px;
      height: 100vh;
      box-shadow: 0 2px 5px 2px #b3b3b3;
      z-index: 1000;
      color: #fff;
      &.menuClosed {
        transform: translateX(100%);
        transition: 0.2s ease-in-out;
        overflow: hidden;
      }
      .xout {
        display: block;
        height: 50px;
        width: 100%;
        padding: 15px 10px 15px 0;
        cursor: pointer;
        text-align: right;
        svg {
          height: 100%;
          width: 50px;
        }
      }
      a {
        color: #fff;
        border-radius: 0;
        padding: 20px;
        &.active-nav-link {
          background: #fff;
          color: #2aaee1;
        }
        &:hover {
          background: #fff;
          color: #2aaee1;
        }
      }
    }
  }
}
</style>
