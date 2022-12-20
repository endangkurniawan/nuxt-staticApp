<template lang="pug">
a.btn.btn-primary.btn(v-if="type === 'submit'" :type="`${type}`") {{ title }}
a.btn.btn-primary.btn(v-else-if="type === 'link'" :type="`${link}`") {{ title }}
</template>

<script>
export default {
  name: 'ButtonApp',
  props: {
    title: String,
    type: String,
    link: String
  }
}
</script>
