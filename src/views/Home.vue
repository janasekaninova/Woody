<template>
  <div class="home">
    <div class="formular" id="app">
      <h2>Chci najít lekce</h2>
      <label for="mesto">Lokalita</label>
      <select class="selector" v-model="filters.selectedDistrict">
        <option value disabled selected>Vyber lokalitu</option>
        <option
          v-for="place in sortedDistricts"
          v-bind:value="place.id"
          v-bind:key="place.id"
        >{{ place.name }}</option>
      </select>

      <label for="styl">Styl tance</label>
      <select class="selector" v-model="filters.selectedStyle">
        <option value disabled selected>Zvol styl tance</option>
        <option
          v-for="dance in style"
          v-bind:value="dance.id"
          v-bind:key="dance.id"
        >{{ dance.name }}</option>
      </select>

      <weekcheck v-on:dayFilterChange="doOnDayFilterChange($event)" />

      <button type="button" v-on:click="search">Vyhledat</button>
    </div>

    <div
      v-if="results.length === 0 && !pageWasLoaded"
      class="netanci"
    >Dnes si odpočiň, stejně se nikde nic neděje.</div>
    <lessonsresults v-else v-bind:dataFromHome="results" />

    <section class="fotogalerie">
      <a href="https://www.danza.cz/">
        <img src="@/Images/logo_danza.png" alt="logo TŠ Danza" />
      </a>
      <a href="https://tsdynamic.cz/">
        <img src="@/Images/logo_dynamic.png" alt="logo TŠ Dynamic" />
      </a>
      <a href="https://www.tanecniskolaeso.cz/">
        <img src="@/Images/logo_eso.png" alt="logo TŠ Eso" />
      </a>
      <a href="http://www.rugcutters.cz/">
        <img src="@/Images/logo_rugcutters.png" alt="logo TŠ Rug Cutters" />
      </a>
      <a href="https://www.starlet-brno.cz/">
        <img src="@/Images/logo_starlet.png" alt="logo TŠ Starlet" />
      </a>
      <a href="http://studiostolarna.cz/stolarna/index.php">
        <img src="@/Images/logo_stolarna.png" alt="logo TŠ Stolárna" />
      </a>
      <a href="https://www.swingwings.cz/">
        <img src="@/Images/logo_swing_wings.png" alt="logo TŠ Swing Wings" />
      </a>
    </section>

    <ourfooter />
  </div>
</template>

<script>
import LessonsResults from "../components/LessonsResults.vue";
import OurFooter from "../components/OurFooter.vue";
import Weekcheck from "../components/Weekcheck.vue";

export default {
  name: "home",
  components: {
    lessonsresults: LessonsResults,
    ourfooter: OurFooter,
    weekcheck: Weekcheck
  },
  data() {
    return {
      districts: [
        { name: "Bohunice", id: 1 },
        { name: "Bosonohy", id: 2 },
        { name: "Bystrc", id: 3 },
        { name: "Černovice", id: 4 },
        { name: "Chrlice", id: 5 },
        { name: "Ivanovice", id: 6 },
        { name: "Jehnice", id: 7 },
        { name: "Brno - Jih", id: 8 },
        { name: "Jundrov", id: 9 },
        { name: "Kníničky", id: 10 },
        { name: "Kohoutovice", id: 11 },
        { name: "Komín", id: 12 },
        { name: "Královo Pole", id: 13 },
        { name: "Líšeň", id: 14 },
        { name: "Maloměřice a Obřany", id: 15 },
        { name: "Medlánky", id: 16 },
        { name: "Nový Lískovec", id: 17 },
        { name: "Ořešín", id: 18 },
        { name: "Řečkovice a Mokrá Hora", id: 19 },
        { name: "Brno - Sever", id: 20 },
        { name: "Slatina", id: 21 },
        { name: "Starý Lískovec", id: 22 },
        { name: "Brno - Střed", id: 23 },
        { name: "Tuřany", id: 24 },
        { name: "Útěchov", id: 25 },
        { name: "Vinohrady", id: 26 },
        { name: "Žabovřesky", id: 27 },
        { name: "Žebětín", id: 28 },
        { name: "Židenice", id: 29 },
        { name: "Černá pole", id: 30 },
        { name: "Zábrdovice", id: 31 }
      ],

      style: [
        { name: "Swing", id: 1 },
        { name: "Latinsko-americké", id: 2 },
        { name: "Standardní", id: 3 }
      ],

      filters: {
        checkedDay: [],
        selectedDistrict: "",
        selectedStyle: ""
      },

      results: [],

      pageWasLoaded: true
    };
  },

  computed: {
    sortedDistricts() {
      return this.districts.sort(function(a, b) {
        var x = a.name.toLowerCase();
        var y = b.name.toLowerCase();
        return x.localeCompare(y);
      });
    }
  },

  methods: {
    doOnDayFilterChange(value) {
      this.filters.checkedDay = value;
    },
    search() {
      this.pageWasLoaded = false;
      fetch("/API/LessonsAPI.json")
        .then(response => response.json())
        .then(data => {
          this.results = data
            .filter(i => i.district === this.filters.selectedDistrict)
            .filter(i => i.danceFamily === this.filters.selectedStyle)
            .filter(i => this.filters.checkedDay.some(day => day === i.day));
          console.log(this.results);
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style>
.home {
  display: flex;
  flex-direction: column;
  padding: 10px;
}

h2 {
  font-family: "Roboto Slab", serif;
  font-size: 36px;
  margin-top: 5px;
}

label {
  font-size: 22px;
  margin: 5px;
  padding: 5px;
}

.formular {
  padding: 10px;
  margin-left: auto;
  margin-right: auto;
  font-family: "Roboto Slab", serif;
  background-color: #f5eec3;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.5);
}
.selector {
  height: 2rem;
  margin-bottom: 30px;
}

button {
  color: #280004;
  background-color: #ffffff;
  font-family: "Roboto Slab", serif;
  font-size: 16px;
  font-weight: bold;
  padding: 10px;
  margin-top: 30px;
  height: 50px;
}

.fotogalerie {
  justify-content: space-between;
  align-items: center;
  display: flex;
  flex-flow: row wrap;
  padding: 40px;
}

.fotogalerie img {
  filter: grayscale(100%);
  transition: 0.4s;
}

.fotogalerie img:hover {
  filter: grayscale(0);
}

.netanci {
  color: #ffffff;
  text-align: center;
  font-family: "Roboto Slab", serif;
  font-size: 36px;
  padding: 25px;
}

body {
  background-color: #050609;
}

/*///////////////////////// tablet ////////////////////////////////*/
@media (min-width: 700px) {
  .menu {
    display: flex;
  }

  .menu li {
    border-bottom: 1px solid #ffffff;
    flex: 0 0 33%;
  }
}

/*///////////////////////// PC ////////////////////////////////*/
@media (min-width: 1100px) {
  .menu {
    padding: 50px 150px;
  }

  .formular {
    width: 1100px;
  }
}
</style>
