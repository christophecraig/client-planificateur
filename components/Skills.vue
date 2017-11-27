<template>
  <ul>
    <li v-for="skill of skills" :key="skill.id">{{skill}}</li>
  </ul>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Skills',
  data() {
    return {
      skills: [],
      errors: [],
    };
  },
  created() {
    // A rajouter dans le get l'id de la resource à consulter, je ne sais pas encore comment
    axios
      .get('http://localhost/~ccraig/planificateur/rest/skills/get')
      .then(response => {
        console.log('test');
        this.skills = response.data;
        console.log(this.skills);
        console.log('lol');
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>