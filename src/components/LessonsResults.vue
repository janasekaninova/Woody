<template>
  <div>
    <cardresults
      v-for="(item, index) in dataFromHome"
      v-bind:cardContent="item"
      v-bind:key="index"
    />
  </div>
</template>

<script>
import CardResults from "./CardResults.vue";
export default {
  name: "lessonsresults",
  components: {
    cardresults: CardResults
  },
  props: ["dataFromHome"]
};
</script>

<style>
</style>