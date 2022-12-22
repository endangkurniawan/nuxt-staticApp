<template lang="pug">
.header
  .container-pluid.mx-3
    .header__wrapper
      ='\n'
      a.header__logo(href="#")
        ='\n'
        img.header__logo__el(src="~/assets/img/logo/logo-header.svg" alt="Logo Image")/
        ='\n'
      ul.header__nav
        li(v-for="(item, index) in menus" :key="index").header__item
          ='\n'
          a.header__link(:href="`${item.route}`")
            | {{ item.name }}
        ButtonAppVue.btn--primary(
          type="link"
          link="/product"
          title="Get Started"
          )| {{ titleBtn }}
</template>

<script>
import ButtonAppVue from './button/ButtonApp.vue'
export default {
  name: 'Header',
  components: {
    ButtonAppVue,
  },
  data() {
    return {
      titleBtn: 'Free Trial',
      menus: [
        {
          name: 'Home',
          route: '#'
        }
      ]
    }
  },
  created() {
    this.getMenus()
  },
  methods: {
    getMenus() {
      const response = [
        {
          name: 'Home',
          route: '#'
        },
        {
          name: 'Example Api',
          route: '/example-api'
        },
        {
          name: 'Product',
          route: '#'
        },
        {
          name: 'Pricing',
          route: '#'
        },
        {
          name: 'About Us',
          route: '#'
        },
        {
          name: 'Blog',
          route: '#'
        },
        {
          name: 'Contact',
          route: '#'
        },
      ]

      this.menus = response
    }
  }
}
</script>

 <style>
.header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  background-color: #fff;
  padding: 24px 0;
}

.container {
  width: 1440px;
  margin: 0 auto;
}

.header__wrapper::after {
  content: '';
  display: table;
  clear: both;
}

.header__logo {
  float: left;
}

.header__nav {
  padding: 0;
  float: right;
  margin: 0 !important;
}

.header__item {
  display: inline-block;
  margin: 8px 32px 8px 0;
}

.header__item:last-child {
  margin-right: 0;
}

.header__link {
  text-decoration: none;
}

.btn--primary {
  float: right;
}

 </style>
