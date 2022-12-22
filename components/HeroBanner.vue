<template lang="pug">
//- Hero banner
.hero-banner
  .container-pluid.mx-3
    .hero-banner__txt
      h2.hero-banner__title
        | {{ title }}
      p.hero-banner__desc
        | {{ desc }}
      ='\n'
      ButtonAppVue.btn--primary(type="link" link="/product" title="Get Started")
      ='\n'
      ButtonAppVue.btn--secondary(type="link" link="/product" title="Contact Us")
    .hero-banner__img
    img.hero-banner__img__el(:src="`${logo}`")
</template>

<script>
import ButtonAppVue from './button/ButtonApp.vue';
export default {
  name: 'HeroBanner',
  components: {
    ButtonAppVue,
  },
  data() {
    return {
      title: 'Grow your Sales and Services',
      desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
      logo: '/img/banner/hero-banner.jpg'
    }
  }
}
</script>

<style lang="scss">
  .container {
    width: 1440px;
    margin: 0 auto;
  }
  .hero-banner {
    background-color: lightgreen;
    padding-top: 50px;
  }

  .hero-banner::after {
    content: '';
    display: table;
    clear: both;
  }

  .hero-banner__txt {
    float: left;
    width: 50%;
  }

  .hero-banner__img {
    float: right;
    width: 50%;
  }

  img {
    width: 100%;
    display: block;
  }

  .btn {
    display: inline-block;
    margin: 0;
  }
</style>
