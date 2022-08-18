<template>
  <div class="floor">
    <v-flat
        v-for="flat in flats"
        :key="flat.id"
        :flat="flat"
        :all-flats="allFlats">
    </v-flat>
  </div>
</template>

<script>
import VFlat from "@/components/Flat/VFlat";

export default {
  name: "VFloor",
  components: {
    VFlat,
  },
  props: ['floorNumber', 'flats', 'allFlats']
}
</script>

<style lang="scss">
.floor {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  gap: 5px;
}
</style>