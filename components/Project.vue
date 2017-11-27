<template>
  <div class="project" :class="{ checked: checked}" @click="toggleState">
      <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Project",
  data() {
    return {
        checked: true
    };
  },
  methods: {
      toggleState() {
          this.checked = !this.checked
      }
  },
  watch: {
      checked () {
          
      }
  }
};
</script>

<style>
.checked {
    background: #DDD;
}
</style>
