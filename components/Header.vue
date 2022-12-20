<template lang="pug">
//- Header
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
          a.header__link(href="#")
            | {{ item.name }}
      a.btn--primary(href="#")
        | {{ titleBtn }}
</template>

<script>
export default {
  name: 'Header',
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
