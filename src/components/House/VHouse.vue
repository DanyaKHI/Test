<template>
  <div class="house">
    <div class="flats_numbers">
      <div class="flats_number"
           v-for="n in floorsCount"
           :key="n">{{ n }}
      </div>
    </div>
    <v-entrance
        v-for="entrance in sortEntrances"
        :key="entrance.id"
        :entrance-id="entrance.id"
        :floors="entrance.floors"
        :entrance-title="entrance.title"
        :flats="flats">
    </v-entrance>
  </div>
</template>

<script>
import VEntrance from "@/components/Entrance/VEntrance";

export default {
  name: "VHouse",
  components: {
    VEntrance
  },
  props: ['houseId', 'entrances', 'flats'],
  computed: {
    sortEntrances: function () {
      return this.entrances.filter(entrance => entrance.house_id === this.houseId)
    },
    floorsCount: function () {
      let max = 0
      let entrances = this.entrances.filter(entrance => entrance.house_id === this.houseId)
      entrances.forEach((entrance) => {
        if (entrance.floors.length > max) max = entrance.floors.length
      })
      return max
    }
  }
}
</script>

<style lang="scss">
.house {
  display: flex;
  flex-direction: row;
  gap: 15px;
  margin-bottom: 15px;
  .flats_numbers{
    display: flex;
    flex-direction: column-reverse;
    gap: 5px;
    justify-content: start;
    .flats_number{
      width: 17px;
      height: 17px;
      font-size: 10px;
      opacity: 0.8;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}
</style>