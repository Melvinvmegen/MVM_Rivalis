<template lang="pug">
section#results.py-md-15.py-10.text-center.section--dark
  .container
    h2.after Les résultats
    br
    h3.mb-10 Les chefs d’entreprises obtiennent des résultats concrets dès la première année
      v-row(v-intersect='statsNumberVisibility' :class="{ 'justify-center': $vuetify.breakpoint.smAndDown }")
        v-col.col-10(md=4)
          h2.text-md-h2.text-h3.font-weight-bold
            number(:from="0" :to="number1" ref="number1" :animationPaused="true")
            span %
          br
          p {{ sentence1 }}
        v-col.col-10(md=4)
          h2.text-md-h2.text-h3.font-weight-bold
            number(:from="0" :to="number2" ref="number2" :animationPaused="true")
            span %
          br
          p {{ sentence2 }}
        v-col.col-10(md=4)
          h2.text-md-h2.text-h3.font-weight-bold
            number(:from="0" :to="number3" ref="number3" :animationPaused="true")
            span %
          br
          p  {{ sentence3 }}

</template>

<script>
export default {
  data() {
    return {
      number1: 95,
      number2: 95,
      number3: 98,
      sentence1: "AUGMENTENT LEUR CHIFFRE D'AFFAIRES",
      sentence2: 'FONT CROITRE LEUR RENTABILITE',
      sentence3: 'AMELIORENT LEUR TRESORERIE'
    }
  },
  methods: {
    statsNumberVisibility(entries) {
      if (entries[0].isIntersecting) {
        this.$refs.number1.play()
        this.$refs.number2.play()
        this.$refs.number3.play()
      }
    },
  }
}
</script>

<style scoped>
  .dashed {
    border: 1px dashed #58585A
  }
</style>