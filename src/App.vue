<template>
  <h1>Vue JS</h1>
  <PenDriveOptionsAPI />
  <PenDriveCompositionAPI
    :selectedCapacity="selectedCapacity"
    :changeSelectedCapacity="changeSelectedCapacity"
    @increaseSelectedCapacity="increaseSelectedCapacity"
  />
</template>

<script>
import PenDriveOptionsAPI from "./components/PenDriveOptionsAPI.vue";
import PenDriveCompositionAPI from "./components/PenDriveCompositionAPI.vue";
import { ref } from "vue";
export default {
  components: {
    PenDriveOptionsAPI,
    PenDriveCompositionAPI,
  },
  setup() {
    let selectedCapacity = ref(8);
    const changeSelectedCapacity = (cap) => {
      selectedCapacity.value = cap;
    };
    const increaseSelectedCapacity = (inc) => {
      selectedCapacity.value += inc;
    };
    return {
      selectedCapacity,
      changeSelectedCapacity,
      increaseSelectedCapacity,
    };
  },
};
</script>

<style></style>
