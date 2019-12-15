<template>
  <div class="karticka">
    <h3>{{ singleGaff.danceSchool }}</h3>
    <div class="detailyNazvy">
      <p>{{ singleGaff.danceFamily }}</p>
      <p>{{ singleGaff.address }}</p>
      <p>{{ singleGaff.time }}</p>
    </div>

    <div class="detailyVysledky">
      <p>
        <font-awesome-icon icon="link" class="icon" />
        <a v-bind:href="singleGaff.link">{{ singleGaff.link}}</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "gaffsresults",
  components: {},
  props: ["singleGaff"]
};
</script>

<style scoped>
.detailyNazvy {
  padding-right: 20px;
}

button {
  color: #280004;
  background-color: #ffffff;
  font-family: "Roboto Condensed", sans-serif;
  font-size: 16px;
  padding: 10px;
}

.karticka {
  display: flex;
  flex-direction: row;
  flex-basis: auto;
  flex-wrap: wrap;
  color: #280004;
  font-size: 24px;
}

a {
  color: #280004;
}
</style>