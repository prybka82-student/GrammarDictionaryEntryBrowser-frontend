<template lang="html">

  <section class="entryRelated">
    <p>Homonimy i wyrazy spokrewnione:</p>
    <ul>
      <li v-for="word in related" :key="word.id">
        {{word.word}}
        <span v-for="category in word.categories" :key="category.id">
          <categoryLabel :name="category.name" :valueFull="category.valueFull" :valueAbbr="category.valueAbbr"></categoryLabel>
        </span>
      </li>
    </ul>
  </section>

</template>

<script lang="js">
import categoryLabel from "./categoryLabel.vue"

  export default  {
    name: 'entryRelated',
    components: {
      categoryLabel
    },
    props: {
      related: {}
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
</style>
