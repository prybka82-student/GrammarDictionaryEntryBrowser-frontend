<template lang="html">

  <section class="entryTable">
    
    <div role="tablist" v-for="table in tables" :key="table.id">
      <b-card no-body class="mb-1">

        <b-card-header header-tag="header" class="p-1" role="tab">
          <b-button block href="#" v-b-toggle="'accordion-' + table.id" variant="info" >
            <span v-for="title in table.titles" :key="title.id">
              {{title.name}}: {{title.valueFull}}
            </span>
          </b-button>
        </b-card-header>

        <b-collapse :id="'accordion-' + table.id" accordion="my-accordion" role="tabpanel">
          <b-card-body>
            <b-card-text>
              
              <!-- <b-table small striped hover :items="table.rows" :fields="table.columnHeaders"> -->
              <b-table small striped hover :items="rowConverter(table.rows)" :fields="headerConverter(table.columnHeaders)">
                
                <template v-slot:cell(_0)="row">
                  <entryCell :cell="row"/>
                </template>

                <template v-slot:cell(_1)="row">
                  <entryCell :cell="row"/>
                </template>

                <template v-slot:cell(_2)="row">
                  <entryCell :cell="row"/>
                </template>

              </b-table>

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
          key:"_" + (0).toString(10),
          label:"",
          sortable:false,
          catName: "",
          catVal: ""
        });

        for (index = 0, len = header.length; index < len; ++index) {
          res.push({
            key: "_" + (index+1).toString(10),
            label: header[index].valueAbbr,
            sortable: false,
            catName: header[index].name,
            catVal: header[index].valueFull
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
