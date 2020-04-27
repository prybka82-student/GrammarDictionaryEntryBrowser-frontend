<template lang="html">

  <section class="entryBrowser">

    <div>
      <b-tabs pills card vertical>
        <b-tab v-for="entry in response" :key="entry.id" :title="entry.lemma">
          <b-card-text>
            <h2>{{entry.lemma}}</h2>
            <h5>{{entry.pos.valueFull}}</h5>
            <p>{{arrayToString(entry.meanings)}}</p>
            <small>paradygmat: <span class="text-monospace">{{entry.paradigm}}</span></small>

            <entryTable :tables="entry.tables"/>

            <entryRelated v-if="entry.relateds.length>0" :related="entry.relateds" />
                        

          </b-card-text>
        </b-tab>
      </b-tabs>

    </div>


  </section>

</template>

<script lang="js">
import axios from 'axios'
import entryRelated from './entryRelated.vue'
import entryTable from './entryTable.vue'

  export default  {
    name: 'entryBrowser',
    components: {
      entryRelated, entryTable
    },
    props: {
      query: {
          type: String
        }
    },
    mounted () {
      
    },
    data () {
      return {
        word: "",
        response: null
      }
    },
    watch: {
      query: function() {
        this.word = this.query;
        console.log("getting data for " + this.word);
        axios
          .get("https://localhost:44320/dictionary/browser/find?form=" + this.word)
          .then(resp => {
            console.log("retrieving data...");
            console.log(resp.status);
            this.response = resp.data;
          })
          .catch(function(error) {
            console.log("ERROR: " + error);
          });
          // .then(response => (this.response = response));        
      }
    },
    methods: {
      arrayToString: function(arr) {
        return arr.join(", ");
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
.entryBrowser {
}
</style>
