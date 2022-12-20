<template lang="pug">
//- Hero banner
.hero-banner
  .hero-banner__txt
    h2.hero-banner__title
      | {{ title }}
    p.hero-banner__desc
      | {{ desc }}
    ButtonAppVue.btn--primary(
      type="link"
      link="/product"
      title="Get Started"
    )
    ButtonAppVue.btn--secondary(
      type="link"
      link="/product"
      title="Contact Us"
    )
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
