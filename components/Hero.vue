<template lang="pug">
.hero.section--light
  v-container.col-lg-6.col-md-8.col-sm-10.col-12.pa-md-0
    TextHeader(:title="title")
    span(v-html="description")
    CTA(v-if="ctaText && link" :className="true" color="accent" :text="ctaText" :link="link")
  v-img.hero-image(:src='require(`~/assets/Michel van Megen.png`)' v-if='this.$vuetify.breakpoint.smAndUp')
  v-img.hero-image(:src='require(`~/assets/Michel van Megen Mini.png`)' v-else)

</template>

<script>
import CTA from '~/components/CTA'
import TextHeader from '~/components/TextHeader'

export default {
  components: {
      CTA,
      TextHeader
  },
  data () {
    return {
      title: 'COACHING, CONSEIL ET ACCOMPAGNEMENT DES DIRIGEANTS D’ENTREPRISES',
      description: 'L’art de la réussite consiste à bien savoir s’entourer…',
      ctaText: 'Contactez-moi',
      link: 'contact'
    }
  }
}
</script>

<style scoped>

  .hero {
    position: relative;
    align-items: center;
    display: flex;
    justify-content: center;
    background-color: transparent;
    margin-top: -6rem;
    min-height: calc(85vh - 6rem);
  }

  .hero-image {
    width: 600px;
    position: absolute;
    bottom: 0;
    right: 10%;
    height: auto;
    z-index: 4;
    border-radius: 4%
  }

  @media (max-width: 1600px) { 
    .hero-image {
      right: 0
    }
  }

  @media (max-width: 1400px) { 
    .hero-image {
      width: 400px
    }
  }

  @media (max-width: 978px) { 
    .hero-image {
      width: 300px
    }
  }

  @media (max-width: 450px) { 
    .hero {
      margin-top: -3rem;
      min-height: calc(100vh - 6rem);
    }

    .hero-image {
      width: 250px
    }
  }

  @media (max-width: 420px) { 
    .hero-image {
      width: 200px
    }
  }

  @media (max-width: 380px) { 
    .hero-image {
      width: 175px
    }
  }

</style>