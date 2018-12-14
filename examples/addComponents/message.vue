<template>
  <div>
      增加消息级别，同一级别只显示一条；
  </div>
</template>

<script>
export default {
  name: 'message',
  mixins: [],
  components: {},
    mounted(){
      let v = this;
      let index =0
       setInterval(()=>{
           index ++;
           v.$mes.error({
               content:`我的是${index}条消息`,
               closable:true,
               level: 5
           })
       },300);

    },
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

<style scoped>

</style>
