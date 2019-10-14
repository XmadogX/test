<template>
<div>
  <h3>Table 1</h3>
  <Table1 :columns="columns" :rows="rows"/>
  <h3>Table 2</h3>
  <Table2 :columns="columns" :rows="rows" :filters="$options.filters"/>
  <h3>Table 3</h3>
  <Table3 :columns="columns" :rows="rows"/>
</div>
</template>

<script>
import Table1 from './components/TestTables/Table1'
import Table2 from './components/TestTables/Table2'
import Table3 from './components/TestTables/Table3'
import moment from 'moment'

export default {
  components: {
    Table1,
    Table2,
    Table3
  },
  data () {
    return {
      columns: [
        { caption: 'ФИО', id: 'fio' },
        { caption: 'Дата рождения', id: 'dob', template: 'date' },
        { caption: 'Страна проживания', id: 'country', template: 'country' }
      ],
      rows: [
        { fio: 'Дэйв Харрисон', dob: 730166400, country: 'us' },
        { fio: 'Лоза Юрий Эдуардович', dob: -502243200, country: 'ru' },
        { fio: 'Меркель Ангела', dob: -487900800, country: 'de' },
        { fio: 'Назарбаев Нурсултан Абишевич', dob: -930614400, country: 'kz' }
      ]
    }
  },
  computed: {
  },
  watch: {
  },
  filters: {
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
<style lang="scss">
  @import "~bootstrap/dist/css/bootstrap.min.css";
</style>
