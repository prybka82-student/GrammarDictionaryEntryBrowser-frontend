<template lang="html">

  <span class="badge badge-pill badge-success"
    v-b-popover.hover.top="description" :title="category">
      {{value}}
    </span>

</template>

<script lang="js">

  export default  {
    name: 'categoryLabel',
    props: {
      value: {},
      description: {},
      category: {}
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
  .categoryLabel {

  }
</style>
