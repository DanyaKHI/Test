<template>
  <div class="checker_board">
    <v-house
        :house-id="houseId"
        :entrances="entrances"
        :flats="flats">
    </v-house>
  </div>
</template>
<script>
import VHouse from "@/components/House/VHouse";

export default {
  name: "CheckerBoard",
  components: {
    VHouse,
  },
  props: ['houseId', 'entrances', 'flats'],
}
</script>

<style lang="scss">

</style>