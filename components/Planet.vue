<template>
  <div>
    <p>
      <span>Planet :</span>
      <input v-model="planet" type="number">
    </p>
    <p>
      <span>Satelit :</span>
      <input v-model="satelit" type="number">
    </p>
    <p>
      <span>Total :</span>
      <input v-model="total" type="number">
    </p>
  </div>
</template>

<script>
export default {
  data: () => ({
    planet: 0,
    satelit: 0
  }),
  computed: {
    total() {
      return parseInt(this.planet) + parseInt(this.satelit)
    }
  }
}
</script>
