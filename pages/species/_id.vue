<template>
  <div>
    <h2>{{ data.name }}</h2>
    <hr>
    <span>
      {{ data.name }} is a {{ data.classification }}. His skin color is {{ data.skin_colors }} and {{ data.hair_colors }} hair colors. He can speak in {{ data.language }} language.
    </span>
  </div>
</template>

<script>
export default {
  async asyncData({ app, params }) {
    const response = await app.$axios.get(
      `https://swapi.co/api/species/${params.id}`
    )
    return {
      data: response.data
    }
  }
}
</script>
