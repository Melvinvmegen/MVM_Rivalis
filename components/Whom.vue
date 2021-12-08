<template lang="pug">
#whom.py-15
  v-container
    h2.text-center.mb-10.text-primary.after Qui suis je ?
    v-row.justify-center
      v-col.col-11(lg=4 md=6 sm=10 v-for='who in Whom' :key='who.name')
        v-card(elevation="3" rounded)
          v-col.d-flex.my-2(md=12)
            v-avatar.mx-auto.border-avatar(color='primary' size='150')
              v-img(:src='require(`~/assets/${who.imgPath}`)' width='150' height='150')
          v-card-title.d-block.text-center {{ who.name }}
          v-card-text.text-center(v-html='who.name == "Michel van Megen" ? mvmText : rivalisText')
    slot

</template>

<script>

export default {
  data() {
    return {
      Whom: [
        { imgPath: 'Michel.jpeg', name: 'Michel van Megen' },
        { imgPath: 'logo_rivalis.png', name: 'Le réseau RIVALIS' },
      ]
    }
  },
  computed: {
    mvmText: function () {
      return `
        "Je suis un manager dynamique qui aime entreprendre. Fort de plus de 20 ans d’expérience
        commercial et en management je cherche un nouveau challenge. Quadrilingues avec une
        bonne connaissance d’autres cultures, j’aime me déplacer et être en première ligne face aux
        clients. Je vous demande qu’à pouvoir montrer mes compétences."
        <br><br>
        Michel Van Megen - Gérant et fondateur de la société
      `
    },
    rivalisText: function () {
      return `
        Plus de 600 conseillers sur toute la France. Les grosses entreprises ont les moyens d'embaucher des cadres et de s'offrir des consultants compétents. C'est un luxe que les petites TPE / PME ne peuvent se permettre. 
        Pourtant, elles en auraient bien besoin.
        Sous l'impulsion d'Henri Valdan, Rivalis a constitué, depuis 1994, un réseau de conseillers triés sur le volet pour leur parcours professionnel, la complémentarité de leurs expériences, et surtout pour leurs qualités humaines. Ces femmes et ces hommes n'hésitent pas à s'investir pleinement pour la réussite de leurs clients.
      `
    }
  }
}
</script>

<style scoped>
  .border-avatar {
    border: 3px solid #254056;
  }
</style>