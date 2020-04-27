<template lang="html">

  <section class="formInput">
    
    <div class="input-group mb-3">
      <!-- <form v-on:submit.prevent="search"> -->
        
        <b-form-input v-on:keyup.enter="search" v-model="query" type="text" class="form-control" :placeholder="placeholder" :aria-label="placeholder" aria-describedby="basic-addon2"/>
        <div class="input-group-append">
          <button v-on:click="search" class="btn btn-outline-secondary" type="button">{{button}}</button>
        </div>
    </div>

  </section>

</template>

<script lang="js">

  export default  {
    name: 'formInput',
    props: [],
    mounted () {

    },
    data () {
      return {
        query:"",
        placeholder:"Wpisz szukany wyraz...",
        button:'Szukaj'
      }
    },
    methods: {
      search: function() {
        // console.log(this.query);
        this.$emit("inputWord", this.query);
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
.formInput {
}
</style>
