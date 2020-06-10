<template lang="html">
  <section class="entryTable">
    <div role="tablist" v-for="table in tables" :key="table.id">
      <b-card no-body class="mb-1">
        <b-card-header header-tag="header" class="p-1" role="tab">
          <b-button block href="#" v-b-toggle="'accordion-' + table.id" variant="info" >
            <span v-for="title in table.titles" :key="title.id">
              <div v-if="title.name!=''">{{title.name}}: {{title.valueFull}}</div>
              <div v-else>formy</div>
            </span>
          </b-button>
        </b-card-header>
        <b-collapse :id="'accordion-' + table.id" accordion="my-accordion" role="tabpanel">
          <b-card-body>
            <b-card-text>
              <table class="table">
                <thead>
                  <tr>
                    <th></th>
                    <th scope="col" v-for="header in table.columnHeaders" :key="header.id">
                    {{header.name}} {{header.valueFull}}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="row in table.rows" :key="row.id">
                    <th>
                      {{row.rowCategory.valueAbbr}}<span v-if="row.rowCategory.name === 'osoba'" >. {{row.rowCategory.name}}</span>
                    </th>
                    <td v-for="cell in row.columns" :key="cell.id">
                      <entryCell :cell="cell" />
                    </td>
                  </tr>
                </tbody>
              </table>
            </b-card-text>
          </b-card-body>
        </b-collapse>
      </b-card>
    </div>
  </section>
</template>

<script lang="js">
import entryCell from './entryCell.vue'

export default  {
  name: 'entryTable',
  components: {
    entryCell
  },
  props: {
    tables: {}
  },
  mounted () {
  },
  data () {
    return {
    }
  },
  methods: {
    headerConverter: function(header) {
      let res = [];
      let index = 0;
      let len = 0;
      res.push({
        name: null,
        valueAbbr: null,
        valueFull: null,
        description: null,
        id: 0
      });
      for (index = 0, len = header.length; index < len; ++index) {
        res.push({
          id: index + 1,
          name: header[index].name,
          valueAbbr: header[index].valueAbbr,
          valueFull: header[index].valueFull,
          description: header[index].description
        });
      }
      return res;
    },
    rowConverter: function(row) {
      let res = [];
      let index = 0;
      let len = 0;
      for (index = 0, len = row.length; index < len; ++index) {
        res.push({
          '_0': row[index].rowCategory.name + " " + row[index].rowCategory.valueFull,
          '_1': row[index].columns[0],
          '_2': row[index].columns[1]
        });
      }
      return res;
    } 
  },
  computed: {
  }
}

</script>
<style scoped lang="css">
.entryTable {
}
</style>
