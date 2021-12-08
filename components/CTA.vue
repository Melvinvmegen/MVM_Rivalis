<template lang="pug">
  .my-5(:class="{centered: centered}")
    a.text-decoration-none.white--text(href='tel:+33788201727' data-cursor-hover data-cursor-mix-blend-mode="difference")
      v-btn(color='primary' large='')
        .white--text
          | {{ text }}
        v-icon.ml-2 fa-phone
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: null
    },
    centered: Boolean,
    link: {
      type: String,
      default: null
    }
  }
}
</script>

<style>
.centered {
  display: flex;
  justify-content: center;
}
</style>
