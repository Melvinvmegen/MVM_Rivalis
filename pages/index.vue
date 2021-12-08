<template lang='pug'>
v-container.pa-0(fluid)
  Hero
  Whom
    .above-the-fold(v-intersect='showMoreContent')
  .below-the-fold(v-if='loadNewContent')
    How
    Results
    #contact.py-md-15.py-10.text-center.position-relative
      .container
        v-row(:class="{ 'justify-center': $vuetify.breakpoint.smAndDown }")
          Partners
          ContactForm
</template>
<script>

import Hero from '~/components/Hero'
import How from '~/components/How'
import Results from '~/components/Results'
import Partners from '~/components/Partners'
import ContactForm from '~/components/ContactForm'

export default {
  components: {
    Hero,
    How,
    Results,
    Partners,
    ContactForm
  },
  data () {
    return {
      loadNewContent: false
    }
  },
  methods: {
    showMoreContent(entries) {
      if (!this.loadNewContent) {
        this.loadNewContent = entries[0].isIntersecting
      }
    }
  }
}
</script>

<style>
  .after:after {
    content: "";
    display: block;
    margin-top: 1rem;
    height: 10px;
    width: 65px;
    border-bottom: 0.1rem solid #d8d8d8;
    margin-left: auto;
    margin-right: auto;
  }

  h2 {
    color: #254056;
    font-size: 2rem;
  }

  .section--light {
    background-color: #F9F9FC;
  }

  .section--dark {
    background-color: #254056;
    color: white !important;
  }

  .section--dark h2 {
    color: white !important;
  }

  .position-relative {
    position: relative;
  }
</style>