<template>
<div>
  <table class="table table-striped">
    <thead class="thead-light">
      <tr>
        <th v-for="column in columns" :key="column.id">
          {{column.caption}}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row,index) in rows" :key="index">
        <td v-for="column in columns" :key="column.id">
          <template v-if="row[column.id]">
            <template v-if="filters[column.template]">
              {{filters[column.template](row[column.id])}}
            </template>
            <template v-else>
              {{row[column.id]}}
            </template>
          </template>
        </td>
      </tr>
    </tbody>
  </table>
</div>
</template>

<script>

export default {
  props: {
    columns: Array,
    rows: Array,
    filters: Object
  },
  data () {
    return {
    }
  },
  filters: {
  },
  computed: {
  },
  watch: {
  },
  methods: {
  }
}
</script>
