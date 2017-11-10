<template>
  <div id="detailedResource">
    <input type="number" min="1" name="id_resource" v-model="resource_id">
      {{resourceInfo}}
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Resource",
  data() {
    return {
      resource_id: 1,
      resource: {},
      errors: []
    };
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
</style>
