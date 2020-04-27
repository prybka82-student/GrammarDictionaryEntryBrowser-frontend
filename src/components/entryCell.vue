<template lang="html">

  <section class="entryCell">
    <div v-for="form in cell.forms" :key="form.id">
      {{form.word}}
      <span v-for="category in form.categories" :key="category.id">
        <categoryLabel :valueFull="category.valueFull" :valueAbbr="category.valueAbbr" :name="category.name" :description="category.description" />
      </span>
    </div>
  </section>

</template>

<script lang="js">
import categoryLabel from "./categoryLabel.vue"

  export default  {
    name: 'entryCell',
    components: {
      categoryLabel
    },
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
