<template>
  <div>
       <span style="margin-right: 3px;" v-show="children !== null">
               <Icon :class="{tran:data.expand}" type="ios-arrow-forward" @click="close(data)"></Icon>
       </span>
      <span :class="{pl18:children === null}">
          <Checkbox
              :value="data.checked"
              :indeterminate="data.indeterminate"
              :disabled="data.disabled || data.disableCheckbox"
              @click.native.prevent="handleCheck"></Checkbox>
      <span >{{data.groupName}}</span>
      </span>
      <div v-if="children !== null" class="tree-item">
          <tree-node
              v-if="data.expand"
              v-for="item in children"
              :data="item"
              :treeKey="treeKey"
          ></tree-node>
      </div>

  </div>
</template>
<script>
export default {
  name: 'tree-node',
  mixins: [],
  props:{
        data:{
            type: Object,
            default () {
                return {};
            }
        },
        treeKey:{
            type:String
        }
    },
  components: {},
  data () {
    return {

    };
  },
  methods: {
      setChecked(data,checked){
          let v = this;
          if(data.childGroups!==null){
              data.childGroups.forEach(item=>{
                  v.$set(item,'checked',checked);
                  v.setChecked(item,checked)
              })
          }
      },
      handleCheck(){
          let v = this;
          v.$set(v.data,'checked',!v.data.checked);
          v.setChecked(v.data,v.data.checked);
      },
      close(data){
          let v = this;
          v.$set(data,'expand',!data.expand);
      }
  },
  computed: {
    children(){
        return this.data[this.treeKey]
    }
  }
};
</script>

<style scoped>
.pl18{padding-left: 12px;}
.tran{transform: rotate(90deg)}
</style>
