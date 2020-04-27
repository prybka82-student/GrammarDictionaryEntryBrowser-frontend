<template lang="html">

  <section class="entryCell">
    {{cell.name}}
    {{cell.forms[0].word}}
    abc
  </section>

</template>

<script lang="js">

  export default  {
    name: 'entryCell',
    props: {
      cell: {}
    },
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .entryCell {

  }
</style>
