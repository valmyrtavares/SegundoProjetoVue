<template>
  <p v-if="api">{{api}}</p>
</template>

<script>
import fetchData from "../mixins/fetchData";
export default {
  name: "aula",
  props: ["aula"],
  mixins: [fetchData],
  created() {
    this.fetchData(`/aula/${this.aula}`);
  },
  beforeRouteUpdate(to, from, next) {
    this.fetchData(`/aula/${to.params.aula}`);
    next();
  }
};
</script>

<style>
</style>