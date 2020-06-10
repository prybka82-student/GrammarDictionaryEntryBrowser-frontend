<template lang="html">
  <span class="badge badge-pill" :style="colorChanger(name)"
    v-b-popover.hover.top="valueFull + getDescription(description)" :title="name">
      {{valueAbbr}}
    </span>
</template>

<script lang="js">
  export default  {
    name: 'categoryLabel',
    props: {
      name: { type: String },
      description: { type: String },
      valueFull: { type: String },
      valueAbbr: { type: String }
    },
    mounted () {
    },
    data () {
      return {
      }
    },
    methods: {
      getDescription: function(description) {
        if (description == null || description == "") return "";
        else return " (" + description + ")";
      },
      colorChanger: function(catName) {
        if (catName==='rodzaj') return 'background-color:green;color:white';
        else if (catName==='deprecjatywność') return 'background-color:red;color:white';
        else if (catName==='budowa formy') return 'background-color:blue;color:white';
        else if (catName==='styl') return 'background-color:#806000;color:white';
        else if (catName==='negacja') return 'background-color:orange;color:black';
        else if (catName==='stopień') return 'background-color:cyan;color:white';
        else if (catName==='uniformizm') return 'background-color:yellow;color:black';
        else if (catName==='poprzyimkowość') return 'background-color:teal;color:black';
        else if (catName==='akcentowość') return 'background-color:blue;color:white';
        else if (catName==='kongruentność') return 'background-color:purple;color:white';
        else if (catName==='wokaliczność') return 'background-color:pink;color:black';
        else return 'color:black;border-color:#2196F3;border:1px solid';
      }
    },
    computed: {      
    }
}

</script>
  <style scoped lang="css">
.categoryLabel {
  align-items: center !important;
}
</style>
