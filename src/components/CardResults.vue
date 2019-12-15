<template>
  <div class="karticka">
    <div class="detailVysledky">
      <h3>{{ cardContent.danceSchool}}</h3>
      <div class="detailyVysledku">
        <p>{{ cardContent.style }}, {{ cardContent.level }}</p>
        <p>{{ cardContent.day }}, {{ cardContent.time }}</p>
        <p>{{ cardContent.duration }},</p>
        <p>{{ cardContent.address }}</p>
      </div>

      <div class="detailyNazvy">
        <p>
          <font-awesome-icon icon="phone" class="icon" />
          Tel:{{ cardContent.tel }}
        </p>
        <p>
          <font-awesome-icon icon="envelope" class="icon" />
          E-mail: {{ cardContent.email }}
        </p>
        <p>
          <font-awesome-icon icon="link" class="icon" />
          <a v-bind:href="cardContent.link">{{ cardContent.link}}</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "cardresults",
  props: ["cardContent"]
};
</script>

<style>
h3 {
  font-family: "Roboto Slab", serif;
  font-size: 25px;
}
.karticka {
  margin-top: 10px;
  margin-left: auto;
  margin-right: auto;
  padding: 10px;
  background-color: #f5eec3;
  box-shadow: 0 3px 10px #F5EEC3(0, 0, 0, 0.5);
  display: flex;
  flex-wrap: wrap;
}

.karticka a {
  flex-basis: auto;
  margin: 16px 20px 0 16px;
  color: #280004;
}

.karticka img {
  border-radius: 10%;
}

.detailyNazvy {
  padding-right: 20px;
}

.detailVysledky {
  display: flex;
  flex-direction: row;
}

.icon {
  padding-right: 15px;
}

/*///////////////////////// PC ////////////////////////////////*/
@media (min-width: 1100px) {
  .karticka {
    max-width: 1100px;
  }
}
</style>