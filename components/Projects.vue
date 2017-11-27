<template>
    <div id="projects-slider">
        <Project v-for="(project, index) in projects" :key="index">
            <h4>{{project.name}}</h4>
        </Project>
    </div>
</template>

<script>
import axios from 'axios'
import Project from './Project'

export default {
    components: {
        Project
    },
  name: 'Projects',
  data() {
      return {
          projects: {
              type: 'object',
              test: 'enorme'
          }
      }
  },
  computed: {
      count () {
          return this.$store.state.count
      }
  },
  created () {
      axios
      .get('static/projects.json')
      .then(response => {
          let currentProjects = []
          console.log(response.data)
              this.projects =  response.data
      })
  }
}
</script>
