<template>
  <div class="app">
    <checker-board
        v-for="house in houses"
        :key="house"
        :house-id="house"
        :entrances="entrances"
        :flats="flats">
    </checker-board>
  </div>
</template>

<script>
import CheckerBoard from "@/components/CheckerBoard";

export default {
  name: 'App',
  components: {
    CheckerBoard
  },
  data() {
    return {
      houses: [],
      entrances: [],
      flats: [],
    }
  },
  created: function () {
    let jsonData = require('./data.json');
    this.houses = jsonData.houses
    this.entrances = jsonData.entrances
    this.flats = jsonData.flats
  },
}
</script>

<style lang="scss">
@import "normalize.css";

.app {
  font-family: 'Roboto', sans-serif;
  padding: 40px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 40px;
  align-items: flex-end;
  justify-content: start;
}
</style>
