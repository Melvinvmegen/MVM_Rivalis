<template lang="pug">
v-col(sm=8)
  v-card.mx-auto.card-contact(width='400')
    v-card-title 
      h3.primary--text Formulaire de contact
    v-card-text
      v-alert(type='success' v-if='sent') 
        p Votre demande de contact a bien été envoyée !
        span Nous vous recontacterons dans les plus brefs délais.
      v-form(ref="signUpForm" v-model="formValidity" @submit.prevent="sendEmail" id='contact-form' v-else)
        v-alert(color='red' type='error' v-if='errorMessage') {{ errorMessage }}
        v-text-field(label='Prénom' name='firstname' v-model='firstname' required :rules='firstnameRules') Prénom 
        v-text-field(label='Nom' name='lastname' v-model='lastname' required :rules='lastnameRules') Nom 
        v-text-field(label='Email' name='email' v-model='email' required :rules='emailRules') Email 
        v-text-field(label='Téléphone' name='phone' v-model='phone' required :rules='phoneRules') Téléphone 
        v-textarea(label='Message' name='message' v-model='message') Message 
    v-card-actions
      v-btn(:disabled="!formValidity" color="primary" form='contact-form' type='submit' v-if='!sent') Envoyer
</template>

<script>
import emailjs from 'emailjs-com'

export default {
  data() {
    return {
      errorMessage: '',
      formValidity: false,
      sent: false,
      firstname: '',
      firstnameRules: [
        value => !!value || 'Le prénom est obligatoire',
        value => value.length > 0 || 'Le prénom doit être valide'
      ],
      lastname: '',
      lastnameRules: [
        value => !!value || 'Le nom est obligatoire',
        value => value.length > 0 || 'Le nom doit être valide'
      ],
      email: '',
      emailRules: [
        value => !!value || "L'email est obligatoire",
        value => value.indexOf('@') !== 0 || "L'email doit être valide !",
        value => value.indexOf('@') || "L'email doit être valide !",
        value => value.indexOf('.') - value.indexOf('@') !== 1 || "L'email doit être valide !",
        value => value.indexOf('.') <= value.length - 3 || "L'email doit être valide !",
      ],
      phone: '',
      phoneRules: [
        value => !!value || 'Le téléphone est obligatoire',
        value => value.length >= 10 || 'Le nom doit être valide',
        value => value.match(/\d/g) || 'Le téléphone doit être valide',
      ],
      message: '', 
    }
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('service_a84azw9', 'template_4f6cvqk', e.target,
        'user_URL0sKmE2k1Uygav4LYat')
      } catch(error) {
        this.errorMessage = "Une erreur s'est produite."
      }
      // Reset form field
      this.formValidity = false
      this.$refs.signUpForm.reset()
      this.sent = true
    }
  }
}
</script>

<style scoped>
  .card-contact {
    width: 400px;
    padding: 50px;
    position: absolute;
    top: -50px;
    z-index: 4;
    right: 25%;
  }
  
  @media (max-width: 1800px) { 
    .card-contact {
      right: 20%;
    }
  }

  @media (max-width: 1400px) { 
    .card-contact {
      right: 15%;
    }
  }

  @media (max-width: 1100px) { 
    .card-contact {
      right: 10%;
    }
  }

  @media (max-width: 978px) { 
    .card-contact {
      position: relative;
      top: unset;
      right: unset;
    }
  }
</style>