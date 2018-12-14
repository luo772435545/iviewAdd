<template>
  <div class="tree-new">
      <tree-node
        v-for="item in treeData"
        :data="item"
        :treeKey="treeKey"
      ></tree-node>
  </div>
</template>

<script>
    import treeNode from './tree-node'
export default {
  name: 'tree',
    props:{
      treeData:{
          type:Array,
          default:[]
      },
        treeKey:{
          type:String,
          default: 'children'
        }
    },
  mixins: [],
  components: {treeNode},
  data () {
    return {

    };
  },
  methods: {

  },
  computed: {

  }
};
</script>

<style>
    .tree-new .tree-item{
        margin: 0;
        padding: 0 0 0 18px;
    }
</style>
<style scoped>

</style>
