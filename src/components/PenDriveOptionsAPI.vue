<template>
  <h2>Pen Drive (old Options API)</h2>
  <p>Marca: {{ brand }}</p>
  <p>Descripción: {{ description.text }}</p>
  <p>Capacidades: {{ capacities }} GB</p>
  <p>Precios: {{ prices }} €</p>
  <p>Capacidad: {{ capacities[0] }} GB</p>
  <button @click="increase(2)">Aumentar</button>
  <button @click="decrease(2)">Disminuir</button>
</template>

<script>
export default {
  data() {
    return {
      brand: "Kingston",
      description: {
        title: "Pendrive",
        text: "Pendrive de buena calidad",
      },
      capacities: [8, 16, 32, 64, 128, 256, 512],
      prices: [5, 10, 15, 20, 25, 30],
    };
  },
  methods: {
    increase(num) {
      this.capacities[0] += num;
    },
    decrease(num) {
      this.capacities[0] -= num;
    },
  },
};
</script>

<style></style>
