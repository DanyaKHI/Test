<template>
  <div class="entrance">
    <v-floor
        v-for="floor in floors"
        :key="floor.floor"
        :flats="floor.flats"
        :all-flats="flats"
        :floor-number="floor.floor">
    </v-floor>
    <span class="title">{{this.entranceTitle}}</span>
  </div>
</template>

<script>
import VFloor from "@/components/Floor/VFloor";

export default {
  name: "VEntrance",
  components: {
    VFloor
  },
  props: ['entranceId', 'flats', 'floors', 'entranceTitle']

}
</script>

<style lang="scss">
.entrance {
  display: flex;
  flex-direction: column;
  gap: 5px;
  justify-content: end;
  .title{
    margin-top: 15px;
    font-size: 10px;
    opacity: 0.8;
  }
}
</style>