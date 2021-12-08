<template lang="pug">
  .col-lg-7.col-12.pa-md-0(:class="{'align-center': $vuetify.breakpoint.smAndDown}")
    h1(:class="{ 'primary-border': color, 'white--text': white, 'after': after }" v-html="title")
    br
    slot
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: null
    },
    side: {
      type: String,
      default: 'left'
    },
    color: Boolean,
    white: Boolean,
    after: {
      type: Boolean,
      default: true
    }
  }
}
</script>

<style scoped>
  h1 {
    font-size: 2.5rem
  }

  h1.after:after {
    margin-left: unset
  }
  
  h2.primary-border:after {
    border-bottom: 0.1rem solid #234A5D !important;
  }

  h2.side-center:after {
    content: "";
    display: block;
    margin: 2rem auto 1rem;
    height: 10px;
    width: 65px;
    border-bottom: 0.1rem solid #d8d8d8;
  }

  h2.side-right:after {
    content: "";
    display: block;
    margin: 2rem 0 1rem auto;
    height: 10px;
    width: 65px;
    border-bottom: 0.1rem solid #d8d8d8;
  }

  span {
    line-height: 1.8;
  }

  @media (max-width: 978px) { 
    h1 {
      font-size: 2rem
    }
  }

  @media (max-width: 450px) { 
    h1 {
      font-size: 1.5rem
    }
  }

  @media only screen and (max-width: 350px) {
  h2 {
    font-size: 1.5rem;
  }

  h2.side-center:after {
    margin: 0.5rem auto 0.5rem;
  }

  h2.side-right:after {
    margin: 0.5rem auto 0.5rem;
  }
}
</style>
