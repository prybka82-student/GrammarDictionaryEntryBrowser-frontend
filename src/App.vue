<template>
  <div id="app">

    <b-jumbotron header-level="5" bg-variant="warning"  >
      <template v-slot:header>ISGJP</template>
      <template v-slot:lead>Inny słownik gramatyczny języka polskiego</template>
      <!-- <hr class="my-24"/> -->
    </b-jumbotron>

    <formInput @inputWord="updateQuery" />

    <entryBrowser :query="word" />

  </div>
</template>

<script>
import formInput from "./components/formInput.vue";
import entryBrowser from "./components/entryBrowser.vue";

export default {
  name: "App",
  components: {
    entryBrowser,
    formInput
  },
  data: function() {
    return {
      word: ""
    }
  },
  methods: {
    updateQuery(value) {
      this.word = value;
    }
  }
};
</script>

<style>
#app {
  max-width: -webkit-calc(800px - (30px * 2));
  max-width: calc(800px - (30px * 2));
  margin-right: auto;
  margin-left: auto;
  padding-right: 30px;
  padding-left: 30px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

.jumbotron {
  margin-top:-30px;
  height:180px;
}


</style>
