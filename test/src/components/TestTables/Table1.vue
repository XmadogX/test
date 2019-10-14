<template>
<div>
  <table class="table table-striped table-dark">
    <thead class="thead-dark">
      <tr>
        <th v-for="column in columns" :key="column.id">
          {{column.caption}}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row,index) in rows" :key="index">
        <td v-for="column in columns" :key="column.id">
          {{
            row[column.id]
              ?$options.methods[column.template]
                ?$options.methods[column.template](row[column.id])
                :row[column.id]
              :''
          }}
        </td>
      </tr>
    </tbody>
  </table>
</div>
</template>

<script>
import moment from 'moment'

export default {
  props: {
    columns: Array,
    rows: Array
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
    date (value) {
      return moment(value).format('DD.MM.YYYY')
    },
    country (value) {
      const countryDict = {
        us: 'США',
        ru: 'Россия',
        de: 'Германия',
        kz: 'Казахстан'
      }
      return countryDict[value]
    }
  }
}
</script>
