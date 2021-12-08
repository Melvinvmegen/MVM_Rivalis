<template lang="pug">
section#how.py-15.section--light
    v-container
    h2.text-center.mb-10.after Comment je travaille ?
    br
    v-row.justify-center
        v-col(lg=2 md=3 v-for='hows in howSchema' :key='hows')
          .section--light
              v-col.d-flex(md=12)
                v-avatar.mx-auto.dashed(color='' size='75')
                    v-icon(x-large color='primary') {{ hows.icon }}
              v-card-subtitle.font-weight-medium.text-center.primary--text.font-weight-bold {{ hows.title }}
              v-card-text.text-center {{ hows.text }}
</template>

<script>
export default {
  data() {
    return {
      howSchema: [
        { icon: 'fa-users', title: 'Notre premier RDV', text: 'Il est gratuit. Faire connaissance, découvrir votre entreprise, identifier et formaliser vos besoins' },
        { icon: 'fa-tasks', title: "Réaliser le plan d'action", text: 'Nous construisons votre prévisionnel en conciliant vos objectifs professionnels et personnels' },
        { icon: 'fa-chart-line', title: 'Accompagnement', text: 'Nous mettons en place un pilotage de votre entreprise, à travers des rendez-vous réguliers, ajustés à vos disponibilités. Je reste bien sûr disponible au téléphone ou par mail entre 2 rendez-vous !' },
        { icon: 'fa-glass-cheers', title: 'Célébrer - Bilan', text: "En fin d'exercice, les améliorations mesurées permettent de se projeter plus sereinement sur l'exercice à venir, prévoir des investissements, embaucher... Et allons trinquer (avec modération) à NOTRE réussite." }
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