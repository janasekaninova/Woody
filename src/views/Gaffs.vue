<template>
  <div>
    <div
      class="tancirnyUvod"
    >Už toho umíš dost a chceš si jenom zatančit, nebo se nanejvýš naučit nějaký ten pohyb navíc? Od toho tu jsou tančírny, kde za drobný peníz získáš prostor na parketu a třeba i radu zkušenějších.</div>

    <div class="day">
      <gaffsday v-for="day in sortedWeek" v-bind:timetable="day" v-bind:key="day.id" />
    </div>

    <ourfooter />
  </div>
</template>

<script>
/* import GaffsResults from '../components/GaffsResults'; */
import GaffsDay from "../components/GaffsDay";
import OurFooter from "../components/OurFooter.vue";

export default {
  name: "gaffs",
  components: {
    gaffsday: GaffsDay,
    ourfooter: OurFooter
  },

  data() {
    return {
      results: []
    };
  },

  methods: {},

  mounted() {
    fetch("/API/GaffsAPI.json")
      .then(response => response.json())
      .then(data => {
        const reduceFce = (mapa, item) => {
          if (!mapa.has(item.day)) {
            mapa.set(item.day, { id: item.day, actions: [] });
          }
          mapa.get(item.day).actions.push(item);
          return mapa;
        };

        this.results = Array.from(data.reduce(reduceFce, new Map()).values());
        console.log(this.results);
      })
      .catch(error => {
        console.log(error);
      });
  },

  computed: {
    sortedWeek() {
      return this.results.sort(function(a, b) {
        return a.id - b.id;
      });
    }
  }
};
</script>

<style>
h2 {
  padding: 20px;
  margin: 5px;
}

h3 {
  padding: 0 50px;
}

p {
  padding: 0 30px;
}

.tancirnyUvod {
  font-size: 22px;
  padding: 20px 40px;
  text-align: center;
  color: white;
}

.day {
  color: white;
}

/*///////////////////////// tablet ////////////////////////////////*/
@media (min-width: 700px) {
  .menu {
    display: flex;
  }

  .menu li {
    border-bottom: 1px solid #ffffff;
    flex: 0 0 25%;
  }
}

/*///////////////////////// PC ////////////////////////////////*/
@media (min-width: 1100px) {
  .menu {
    padding: 50px 150px;
  }
}
</style>