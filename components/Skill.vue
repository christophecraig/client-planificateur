<template>
  <label :class="{ checked: checked }">
      <input type="checkbox" id="skillChecked" v-model="checked"><slot></slot>
  </label>
</template>

<script>
import axios from 'axios'


export default {
  name: 'Skills',
  data() {
    return {
        checked: true
    };
  }
};
</script>