<template>
  <div id="detailedResource" @click="openModal">
    <sweet-modal ref='modal'>
      <h2>Trouver une ressource</h2>
    <input type="number" min="1" name="id_resource" @keydown="isNumber" v-model="resource_id">
    <div v-if="resource.firstname">
      <h4>{{resource.firstname}} {{resource.name}}</h4>
      <h5><em>{{resource.alias}}</em></h5>

      <p>Efficacité globale : {{resource.efficiency}}</p>
      <div>Détail : 
        <table>
          <tbody>
          <tr><th v-for="skill in resource.skills" :key="skill.name">{{skill.name}}</th></tr>
          <tr><td v-for="skill in resource.skills" :key="skill.name + 'Value'">{{skill.efficiency}}</td></tr>
          </tbody>
        </table>

      </div>
      
      <p><span v-if="resource.available === '1'">Disponible</span>
      <span v-else>Indisponible</span></p>
      </div>
      <h4 v-else-if="resource_id">L'id saisi est incorrect.</h4>
      <h4 v-else>Veuillez saisir un id de ressource.</h4>
</sweet-modal>
  </div>
</template>

<script>
import axios from "axios";
import { SweetModal, SweetModalTab } from "sweet-modal-vue";

export default {
  name: "Resource",
  components: {
    SweetModal,
    SweetModalTab
  },
  data() {
    return {
      resource_id: 0,
      resource: {},
      errors: []
    };
  },
  methods: {
    openModal() {
      this.$refs.modal.open();
    }, 
    // Gérer le cas où la touche appuyée n'est pas un nombre ( '+', '-', '/', '*', '%', '.', ',')
    isNumber(e) {
        console.log(parseInt(e.key))
      if (parseInt(e.key != NaN)) {
        e.prevent();
        e.stop();
      } 
    }
  },
  watch: {
    // Chaque fois que resource_id est modifié, on exécute la fonction suivante qui va chercher en base la resource d'id correspondant
    resource_id() {
      axios
        .get(
          "http://192.168.0.50/~ccraig/planificateur/rest/resource/get/" +
            this.resource_id
        )
        .then(response => {
          console.log(response.data);
          this.resource = response.data;
        })
        .catch(e => {
          this.errors.push(e);
        });
    }
  },
  computed: {
    // Permet de mettre à jour automatiquement l'affichage sans avoir à surveiller this.resource
    resourceInfo() {
      return this.resource.firstname + " " + this.resource.name;
    }
  },
  created() {
    this.resource_id = 1;
  }
  // created() {
  //   console.log(this)
  //   axios
  //     .get("http://localhost/~ccraig/planificateur/rest/resource/get/" + this.resourceId)
  //     .then(response => {
  //       console.log(response.data);
  //       this.resource = response.data;
  //     })
  //     .catch(e => {
  //       this.errors.push(e);
  //     });
  // }
};
</script>

<style lang="scss">
#detailedResource {
  position: fixed;
  z-index: 1;
  bottom: 20%;
  top: 20%;
  left: 20%;
  right: 20%;
}

.sweet-content-content {
  text-align: left;
}

em {
  // text-align: center;
}
</style>
