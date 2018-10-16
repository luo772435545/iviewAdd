<template>
    <div>
        <connt class="connt" :decimals="2" :startVal="0" :usegroup='isTrue' :end="end"></connt>
        <connt class="connt"  :startVal="0" :usegroup='isTrue' :end="end"></connt>
    </div>
</template>

<script>
    import connt from './count/' ;
    export default {
        name: 'countView',
        mixins: [],
        components: {
            connt
        },
        data() {
            return {
                end:'1000'
            };
        }
    };
</script>

<style scoped>

</style>
