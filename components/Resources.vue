<template>
  <div>
    <Skills></Skills>
  <ul>
      <li v-for="resource of resources" :key="resource.id" ><!--@click="expand(resource.id)"-->
          {{resource.alias}}
      </li>
  </ul>
  </div>
</template>

<script>
import axios from "axios";
import Skills from './Skills'

export default {
  name: "Resources",
  components: {
    Skills
  },
  data() {
    return {
      resources: [],
      errors: []
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
  },
  methods: {
      expand (id) {
          
          console.log(id)
      }
  }
};
</script>