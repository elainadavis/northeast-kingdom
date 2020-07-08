<template>
  <div class="header">
    <div class="header-left">
      <a href="/" class="logo">
        <img src="~assets/images/client.jpg" />
      </a>
      Twispworks
    </div>
    <div class="header-right">
      <nuxt-link v-for="page in pages" v-bind:key="page.name" v-html="page.name" :to="`/${page.slug}`"></nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      pages: [
        {
          name: "Document Library",
          slug: "library"
        },
        {
          name: "Important Dates",
          slug: "calendar"
        },
        {
          name: "Recent News",
          slug: "news"
        },
        {
          name: "Community Survey",
          slug: "survey"
        },
        {
          name: "Contact Us",
          slug: "contact"
        }
      ]
    };
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
