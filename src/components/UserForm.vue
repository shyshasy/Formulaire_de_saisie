<template>
  <div class="form-wrapper">
    <div class="form-container">
      <h1>Inscription Hayoma</h1>
      <form @submit.prevent="validateForm">
        <div class="form-group">
          <label for="name">Nom :</label>
          <input type="text" v-model="name" id="name" />
          <span v-if="errors.name" class="error">{{ errors.name }}</span>
        </div>

        <div class="form-group">
          <label for="email">Email :</label>
          <input type="email" v-model="email" id="email" />
          <span v-if="errors.email" class="error">{{ errors.email }}</span>
        </div>

        <div class="form-group">
          <label for="phone">Téléphone :</label>
          <input type="text" v-model="phone" id="phone" />
          <span v-if="errors.phone" class="error">{{ errors.phone }}</span>
        </div>

        <div class="button-container">
          <button type="submit" class="submit-button">Soumettre</button>
        </div>

        <div v-if="successMessage" class="success-message">{{ successMessage }}</div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      errors: {},
      successMessage: '',
    };
  },
  methods: {
    validateForm() {
      this.errors = {};
      if (!this.name) {
        this.errors.name = "Le nom est requis.";
      }
      if (!this.email || !this.validEmail(this.email)) {
        this.errors.email = "Un email valide est requis.";
      }
      if (!this.phone || !this.validPhone(this.phone)) {
        this.errors.phone = "Un numéro de téléphone valide est requis.";
      }

      if (!Object.keys(this.errors).length) {
        this.successMessage = "Formulaire soumis avec succès !";
      }
    },
    validEmail(email) {
      const re = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
      return re.test(email);
    },
    validPhone(phone) {
      const re = /^[0-9]{10}$/;
      return re.test(phone);
    }
  }
};
</script>

<style scoped>
/* Conteneur général centré et pleine hauteur */
.form-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90%;
}

/* Formulaire */
.form-container {
  width: 70vw;
  padding: 60px;
  background-color: #ffffff;
  border-radius: 60px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
  background-image: linear-gradient(to right, #00c6ff, #0072ff);
  color: #333;
}

/* Titre */
h1 {
  font-family: 'Georgia', serif;
  font-size: 36px;
  margin-bottom: 30px;
  color: #ffffff;
  text-align: center;
}

/* Groupes de champs */
.form-group {
  display: flex;
  align-items: center;
  margin-bottom: 40px;
}

/* Style des labels */
label {
  width: 18%; /* Réduction de la largeur des labels pour moins d'espace à gauche */
  font-size: 20px;
  color: #ffffff;
  text-align: right;
  margin-right: 30px; /* Réduction de l'espacement entre le label et le champ */
}

/* Style des champs de saisie */
input {
  width: 70%;
  padding: 15px;
  border: 2px solid #0072ff;
  border-radius: 8px;
  font-size: 18px;
  background-color: #f0f4f8;
}

/* Messages d'erreur */
.error {
  color: #ff5252;
  font-size: 16px;
  margin-top: 5px;
  display: block;
}

/* Conteneur du bouton de soumission */
.button-container {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

/* Bouton de soumission */
.submit-button {
  padding: 20px 40px; /* Augmentation de la taille du bouton */
  background-color: #0072ff;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  font-size: 22px; /* Augmentation de la taille de la police */
  cursor: pointer;
  width:40%;
}

.submit-button:hover {
  background-color: #005bb5;
}

/* Message de succès */
.success-message {
  margin-top: 30px;
  font-size: 20px;
  color: #00e676;
  text-align: center;
}
</style>
