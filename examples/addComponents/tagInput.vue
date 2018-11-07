<template>
    <div>
        <tag-input :tag="tags"></tag-input>
        {{tags}}
    </div>
</template>
isTrue
<script>
    import tagInput from './tagInput/' ;
    export default {
        name: 'tagInputView',
        mixins: [],
        components: {
            tagInput
        },
        data() {
            return {
                tags: [],
            };
        },
        methods:{
            tagsMt (data) {
                this.tags = data;
            }
        }
    };
</script>

<style scoped>

</style>
