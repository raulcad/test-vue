<template>
  <h2>Pen Drive (new Composition API)</h2>
  <p>Marca: {{ brand }}</p>
  <p>Descripción: {{ description.text }}</p>
  <!-- <p>Capacidades: {{ capacities }} GB</p> -->
  <p>Capacidades:
    <!-- <ul>
      <li v-for="(capacity, index) in capacities" :key="index">{{ capacity }} GB</li>
    </ul> -->
    <!-- <ul>
      <li v-for="capacity in capacities" :key="capacity">{{ capacity }} GB</li>
    </ul> -->
    <ul>
      <template v-for="capacity in capacities" :key="capacity">
        <li v-if="capacity <= 32">HC {{ capacity }} GB</li>
        <li v-else-if="capacity === 64">XC {{ capacity }} GB (Standard)</li>
        <li v-else>XC {{ capacity }} GB</li>
      </template>
    </ul>
    HC:
    <ul>
      <template v-for="capacity in capacities" :key="capacity">
        <li v-if="capacity <= 32">{{ capacity }} GB</li>
      </template>
    </ul>
    XC:
    <ul>
      <template v-for="capacity in capacities" :key="capacity">
        <li v-if="capacity > 32">{{ capacity }} GB</li>
      </template>
    </ul>
  </p>
  <p>Precios: {{ prices }} €</p>
  <p>Capacidad: {{ capacity }} GB / {{ selectedCapacity }} GB</p>
  <button @click="increase(2)">Aumentar</button>
  <button @click="decrease(2)">Disminuir</button>
  <button @click="changeSelectedCapacity(16)">Cambiar selección a 16 GB</button>
</template>

<script>
import { ref } from "vue";

export default {
  props: {
    //selectedCapacity: Number,
    selectedCapacity: {
      type: Number,
      default: 8,
    },
    changeSelectedCapacity: Function,
  },
  emits: ["increaseSelectedCapacity"],
  //setup() {
  //setup(props) {
  setup(props, context) {
    const brand = "SanDisk";
    const description = {
      title: "Pendrive",
      text: "Pendrive de alta calidad",
    };
    const capacities = [8, 16, 32, 64, 128, 256, 512];
    const prices = [5, 10, 15, 20, 25, 30];
    console.log(props);
    let capacity = ref(props.selectedCapacity);

    const increase = (num) => {
      capacity.value += num;
      props.changeSelectedCapacity(props.selectedCapacity + num);
    };

    const decrease = (num) => {
      capacity.value -= num;
      context.emit("increaseSelectedCapacity", -num);
    };

    return {
      brand,
      description,
      capacities,
      prices,
      capacity,
      increase,
      decrease,
    };
  },
};
</script>

<style></style>
