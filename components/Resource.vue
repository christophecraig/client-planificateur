<template>
  <div id="detailedResource">
      {{resource.firstName}} {{resource.name}}
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Resource",
  data() {
    return {
      resource: {},
      errors: []
    };
  },
  props: {

  },
  created() {
    axios
      .get("http://localhost/~ccraig/planificateur/rest/resource/get/40")
      .then(response => {
        console.log(response.data);
        this.resource = response.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
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
