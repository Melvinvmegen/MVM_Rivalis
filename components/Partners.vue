<template lang="pug">
  v-col(md=6 sm=8)
    h2 Contactez-nous pour un audit gratuit et sans engagement
    br
    h1 MVM
    br
    .d-flex.justify-center
      v-icon fa-phone
      h4.text-center
        a.ml-2.text-decoration-none(href='tel:+33788201727') 07 88 20 17 27
    .d-flex.justify-center
      v-icon fa-envelope
      h4.text-center
        a.ml-2.text-decoration-none(href='mailto:michel.van.megen@gmail.com') Michel.van.megen@gmail.com
    h2.my-10 En partenariat avec :
    v-row.my-10
      v-col(md=4 v-for='partner in partners')
        v-img.mx-auto(:src='require(`~/assets/${partner}.png`)' max-height="120" max-width="120")
</template>

<script>
export default {
  data() {
    return {
      partners: [
        'henrri',
        'rivalis_mo',
        'rivalis'
      ]
    }
  }

}
</script>

<style scoped>
  .dashed {
    border: 1px dashed #58585A
  }
</style>