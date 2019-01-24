<template>
  <div>
      传入String 不报错
      //如果用于Table render 要先注册
      <IptNub :value="nub"></IptNub>
      <Table :columns="columns" :data="data"></Table>
  </div>
</template>

<script>
    import editInput from  './editInput/editInput'
    import IptNub from './input-number/input-number'
export default {
  name: 'editInputC',
  mixins: [],
  components: {editInput},
  data () {
    return {
        nub:'arqr',
        columns:[ {
            key:'a',
            align: 'center',
            render(h,params) {

                return h('IptNub',{
                    props:{
                        value:params.row.a
                    }
                });
            }
        }],
        data:[{
            a:'a'
        },{
            a:'1'
        },{
            a:'2'
        }],
        obj:{
            val:'123'
        }
    };
  },
  methods: {
      clickMt(){
          console.log('123')
      }
  },
  computed: {

  }
};
</script>

<style scoped>

</style>
