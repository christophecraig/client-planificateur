<template>
<div class="login-box">
<div class="btn" @click="openLoginBox">Se connecter</div>
<sweet-modal ref="login">
  <form method="POST">
      <label for="login">Identifiant</label><input type="text" name="login" id="login" v-model="login">
      <label for="password">Mot de passe</label><input type="text" name="password" id="password" v-model="password">
      <input type="button" value="Valider" @click="connect">
  </form>
</sweet-modal>
</div>
</template>

<script>
import axios from "axios";
import { SweetModal, SweetModalTab } from "sweet-modal-vue";

export default {
  name: "Login",
  components: {
    SweetModal,
    SweetModalTab
  },
  data() {
    return {
      login: "",
      password: "",
      errors: []
    };
  },
  methods: {
    openLoginBox() {
      this.$refs.login.open();
    },
    connect() {
        axios
        .post('http://localhost/~ccraig/planificateur/rest/login/login', {
          login: this.login,
          password: this.password
        })
        .then(response => {
            console.log(response)
        })
        .catch(e => {
            this.errors.push(e)
        })
    }
  }
};
</script>
