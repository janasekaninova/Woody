<template>
  <div>
    <h2>{{ nameOfDays}}</h2>
    <gaffsresults
      v-for="(action, index) in timetable.actions"
      v-bind:singleGaff="action"
      v-bind:key="index"
    />
  </div>
</template>

<script>
import GaffsResults from "./GaffsResults.vue";
export default {
  name: "gaffsday",
  components: {
    gaffsresults: GaffsResults
  },
  props: ["timetable"],

  computed: {
    nameOfDays: function() {
      switch (this.timetable.id) {
        case 1:
          return "Pondělí";
        case 2:
          return "Uterý";
        case 3:
          return "Středa";
        case 4:
          return "Čtvrtek";
        case 5:
          return "Pátek";
        case 6:
          return "Sobota";
        case 7:
          return "Neděle";
      }
    }
  }
};
</script>

<style>
</style>