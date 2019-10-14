<template>
<div class="w-100" style="height: 30vh;">
  <ag-grid-vue
    style="width: 100%;height: 100%"
    class="ag-theme-balham"
    rowSelection="single"
    :columnDefs="mapColumns"
    :rowData="rows"
    @grid-ready="onGridReady"
    :multiSortKey="multiSortKey"
    :defaultColDef="defaultColDef"
  >
  </ag-grid-vue>
</div>
</template>

<script>
import { AgGridVue } from 'ag-grid-vue'
import moment from 'moment'

export default {
  components: {
    AgGridVue
  },
  props: {
    columns: Array,
    rows: Array
  },
  data () {
    return {
      multiSortKey: 'ctrl',
      defaultColDef: {
        sortable: true,
        resizable: true
      }
    }
  },
  computed: {
    mapColumns () {
      return this.columns.map(el => ({
        headerName: el.caption,
        field: el.id,
        width: 10,
        cellRenderer: this.$options.filters[el.template]
      }))
    }
  },
  watch: {
  },
  filters: {
    date ({ value }) {
      return moment(value).format('DD.MM.YYYY')
    },
    country ({ value }) {
      const countryDict = {
        us: 'США',
        ru: 'Россия',
        de: 'Германия',
        kz: 'Казахстан'
      }
      return countryDict[value]
    }
  },
  methods: {
    onGridReady (params) {
      params.api.sizeColumnsToFit()
    }
  }
}
</script>
<style scoped lang="scss">
  @import "~ag-grid-community/dist/styles/ag-grid.css";
  @import "~ag-grid-community/dist/styles/ag-theme-balham.css";
</style>
