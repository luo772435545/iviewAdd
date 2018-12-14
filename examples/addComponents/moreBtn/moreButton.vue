<template>
    <div>
        <div class="moreBtn">
            <Button class="firBtn" ref="mButton" @click="data.btn.clickFn()">{{data.btn.text}}</Button>
            <Select v-model="model"
                    :style="style"
                    transfer
                    v-show="data.list&&data.list.length>0">
                <Option
                    v-for="(item,index) in data.list"
                    v-show="!item.hide"
                    :value="item.value"
                    @click.native="item.clickFn"
                    :key="index">{{ item.text }}
                </Option>
            </Select>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'moreButton',
        props: {
            data: {
                type: Object
            }
        },
        mounted() {
            this.wid = this.$refs.mButton.$el.offsetWidth;
        },
        data() {
            return {
                wid: '',
                model: ''
            };
        },
        computed: {
            style() {
                return {
                    width: (this.wid + 16) + 'px'
                };
            }
        },
        methods: {}

    };
</script>

<style>
    .moreBtn .ivu-select-arrow {
        right: 1px;
    }

    .moreBtn .ivu-select-selection:hover, .moreBtn .ivu-select-selection-focused {
        border-color: #dcdee2;
        background-color: #eee
    }

    .moreBtn .ivu-select-visible .ivu-select-selection {
        border-color: #dcdee2;
        box-shadow: 0 0 0 0
    }
</style>
<style scoped>
    .moreBtn {
        position: relative;
        height: 32px;
    }

    .moreBtn .firBtn {
        position: absolute;
        left: 0;
        top: 0;
        z-index: 5
    }
</style>
