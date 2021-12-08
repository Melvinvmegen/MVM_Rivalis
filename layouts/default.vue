<template lang='pug'>
  v-app(light='')
    v-app-bar(:clipped-left='clipped' fixed='' app='' elevate-on-scroll color='white')
      v-container
        v-row.align-center
          v-col(sm=2)
            v-btn(text rounded :to="{ path: '/', hash:`#app`}" ) {{ title }}
          v-col(md=2)
          v-col.d-flex.justify-space-around(md=5 sm=2 v-if="this.$vuetify.breakpoint.mdAndUp")
            v-btn(v-for='item in navItems' :key='item.text' text rounded :to="{ path: '/', hash:`#${item.anchorLink}`}" ) {{ item.text }}
          v-col.d-flex.justify-space-around(md=5 sm=2 v-else)
            v-app-bar-nav-icon(@click.stop='drawer = !drawer')
      v-navigation-drawer(v-model='drawer' absolute='' temporary='' fixed right)
        v-icon.float-right.mr-4.mt-4(@click.stop="drawer = false") mdi-close
        br
        v-list(nav='' dense='')
          v-list-item-group
            v-list-item.nav-anim(v-for='item in navItems' :key='item.text' two-line exact :to="{ path: '/', hash:`#${item.anchorLink}`}")
              v-list-item-content
                v-list-item-title.ml-4.text-h6.primary--text {{ item.text }}
            v-divider
            br
            .d-flex.justify-center.align-center(:class="{'flex-column': $vuetify.breakpoint.smAndDown}")
              h3.primary--text Michel van Megen
              a.email(href="mailto:michel.van.megen@gmail.com") michel.van.megen@gmail.com
              .icons

    v-main
      nuxt

    v-footer.flex-row.justify-center(color='primary' padless absolute bottom)
      span.white--text &copy; {{ new Date().getFullYear() }}

</template>

<script>
export default {
  head() {
    return {
      title: "Coaching pour dirigeants et chefs d'entreprises",
      meta: [
        { 
          hid: 'description',
          name: 'description',
          content: "Développez votre entreprise, sa rentabilité, son chiffre d'affaires, sa trésorerie avec notre accompagnement coaching sur mesure. Audit gratuit sans engagement."
        }
      ]
    }
  },
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      miniVariant: false,
      right: true,
      title: 'MVM Rivalis',
      navItems: [
        { text: 'Qui suis-je ?', anchorLink: 'whom' },
        { text: 'Comment je travaille ?', anchorLink: 'how' },
        { text: 'Contact', anchorLink: 'contact' }
      ]
    }
  }
}
</script>

<style>
  @font-face {
    font-family: 'Montserrat';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url('~assets/Montserrat-Regular.ttf') format('truetype');
  }

  .v-application a {
    text-decoration: none;
  }

  .v-application {
    font-family: 'Montserrat', sans-serif;
  }

  .v-overlay__scrim {
    height: 100vh !important;
  }

  .v-navigation-drawer {
    height: 100vh !important;
    width: 60vw !important;
  }

  @media (max-width: 450px) { 
    .v-navigation-drawer {
      width: 100vw !important
    }
  }
</style>