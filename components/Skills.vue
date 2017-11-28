<template>
  <ul>
    <Skill v-for="skill of skills" :key="skill.id">
      {{skill.name}}
    </Skill>
  </ul>
</template>

<script>
import axios from 'axios'
import Skill from './Skill'


export default {
  name: 'Skills',
  components: {
    Skill
  },
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
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>