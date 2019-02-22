<template>
  <div>
    <h4>Jumlah planet dan satelit alam</h4>
    <hr>
    <planet />
  </div>
</template>

<script>
const planet = () => import('@@/components/Planet')

export default {
  components: { planet }
}
</script>
