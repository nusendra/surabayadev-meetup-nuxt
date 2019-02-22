<template>
  <div>
    <span> Total Data : {{ datas.count }} </span>
    <no-ssr>
      <table class="table table-hover">
        <thead>
          <tr>
            <th>Name</th>
            <th>Classification</th>
            <th>Skin Colors</th>
            <th>Language</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in datas.results" :key="index">
            <td> {{ item.name }} </td>
            <td> {{ item.classification }} </td>
            <td> {{ item.skin_colors }} </td>
            <td> {{ item.language }} </td>
            <td>
              <button class="btn btn-primary" @click="detail(item.url)">
                Detail
              </button>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <button v-if="datas.previous" class="btn btn-warning" @click="next(datas.previous)">
            Previous
          </button>
          <button v-if="datas.next" class="btn btn-warning" @click="next(datas.next)">
            Next
          </button>
        </tfoot>
      </table>
    </no-ssr>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const response = await app.$axios.get('/species')
    return {
      datas: response.data
    }
  },
  methods: {
    async next(val) {
      console.log(val)
      const response = await this.$axios.get(val)
      this.datas = response.data
    },
    detail(val) {
      const id = val.replace(/[^0-9]/g, '')
      this.$router.push(`/species/${id}`)
    }
  }
}
</script>
