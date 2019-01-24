<template>
  <div>
      <buttons :data="buttonsData" @btnClick="btnClick" :value.sync="value"></buttons>
      <p>{{item}}</p>
  </div>
</template>

<script>
    import buttons from './buttons/'
export default {
  name: 'buttonGroups',
  components: {buttons},
  data () {
    return {
        value:'1',
        buttonsData:[{
            tit: '文字',
            value: '0'
        }, {
            tit: '按钮',
            value: '1'
        }, {
            tit: '按钮1',
            value: '2'
        }],
        item:''
    };
  },
  methods: {
      btnClick(item,data){
          this.item = item;
      }
  },
  computed: {

  }
};
</script>

<style scoped>

</style>
