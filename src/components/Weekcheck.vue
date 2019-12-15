<template>
  <fieldset>
    <legend>Jaký den mi vyhovuje?</legend>
    <div class="checkboxArea">
      <div class="days">
        <input
          type="checkbox"
          id="monday"
          name="monday"
          value="monday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="monday">Pondělí</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="tuesday"
          name="tuesday"
          value="tuesday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="tuesday">Úterý</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="wednesday"
          name="wednesday"
          value="wednesday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="wednesday">Středa</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="thursday"
          name="thursday"
          value="thursday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="thursday">Čtvrtek</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="friday"
          name="friday"
          value="friday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="friday">Pátek</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="saturday"
          name="saturday"
          value="saturday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="saturday">Sobota</label>
      </div>
      <div class="days">
        <input
          type="checkbox"
          id="sunday"
          name="sunday"
          value="sunday"
          class="checkbox"
          v-model="checkedDay"
        />
        <label for="sunday">Neděle</label>
      </div>
    </div>
  </fieldset>
</template>



<script>
export default {
  name: "weekcheck",
  data() {
    return {
      checkedDay: []
    };
  },
  watch: {
    checkedDay: function(value) {
      this.$emit("dayFilterChange", value);
    }
  }
};
</script>



<style>
legend {
  font-size: 22px;
  margin: 5px;
  padding: 5px;
}

fieldset {
  padding: 5px;
}

.checkbox {
  width: 1.2rem;
  height: 1.2rem;
}
/*///////////////////////// tablet ////////////////////////////////*/
@media (min-width: 700px) {
  .checkboxArea {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}
</style>