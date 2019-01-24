<template>
    <tr>
        <td v-for="key in columns" >{{item[key.key]}}</td>
    </tr>
</template>

<script>

export default {
  name: 'tr-no',
  mixins: [],
  components: {},
    props:[columns,data],
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
