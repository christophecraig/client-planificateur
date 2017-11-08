<template>
  <ul>
      <li v-for="resource of resources" :key="resource.id">
          {{resource.name}}
      </li>
  </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "Resources",
  data() {
    return {
        resources: [],
        errors: [],
    };
  },
  created() {
    // A rajouter dans le get l'id de la resource à consulter, je ne sais pas encore comment
    console.log("test");
    axios
      .get("http://localhost/~ccraig/planificateur/rest/resource/get")
      .then(response => {
        this.resources = response.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>
