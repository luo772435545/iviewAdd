<template>
    <div>
        <!--<div class="moreBtn">
            <Button class="firBtn" ref="mButton">按钮</Button>
            <Select v-model="model8"  :style="style" >
                <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
            </Select>
        </div>-->
      <!--  <more-btn :data="datas"></more-btn>-->
        <Table :columns="columns1" :data="data1"></Table>
        <pre>
            {
                        title:'操作',
                        render(h,params){
                            return h('moreBtn',{
                                props:{
                                    data:{
                                        btn:{
                                            text:'查看',
                                            clickFn:()=>{
                                                v.$Message.success('查看'+params.row.name)
                                            }
                                        },
                                        list:[
                                            {
                                                text:'编辑',
                                                value:0,
                                                clickFn:()=>{
                                                    v.$Message.success('编辑')
                                                }
                                            },
                                            {
                                                text:'详情',
                                                value:1,
                                                clickFn:()=>{
                                                    v.$Message.success('详情')
                                                }
                                            }
                                        ]
                                    }
                                }
                            })
                        }
                    }
        </pre>
    </div>
</template>

<script>
    import moreBtn from './moreBtn/'
    export default {
        name: 'moreButtonView',
        mixins: [],
        components: {
            moreBtn
        },
        mounted(){
           // this.wid=this.$refs.mButton.$el.offsetWidth;
        },
        data() {
            let v=this;
            return {
                datas:{
                    btn:{
                        text:'查看',
                        clickFn:()=>{
                            this.$Message.success('查看')
                        }
                    },
                    list:[
                        {
                            text:'编辑',
                            value:0,
                            clickFn:()=>{
                                this.$Message.success('编辑')
                            }
                        },
                        {
                            text:'详情',
                            value:1,
                            clickFn:()=>{
                                this.$Message.success('详情')
                            }
                        }
                    ]
                },

                columns1: [
                    {
                        title: 'Name',
                        key: 'name'
                    },
                    {
                        title: 'Age',
                        key: 'age'
                    },
                    {
                        title: 'Address',
                        key: 'address'
                    },
                    {
                        title:'操作',
                        render(h,params){
                            return h('moreBtn',{
                                props:{
                                    data:{
                                        btn:{
                                            text:'查看',
                                            clickFn:()=>{
                                                v.$Message.success('查看'+params.row.name)
                                            }
                                        },
                                        list:[
                                            {
                                                text:'编辑',
                                                value:0,
                                                clickFn:()=>{
                                                    v.$Message.success('编辑')
                                                }
                                            },
                                            {
                                                text:'详情',
                                                value:1,
                                                clickFn:()=>{
                                                    v.$Message.success('详情')
                                                }
                                            }
                                        ]
                                    }
                                }
                            })
                        }
                    }
                ],
                data1: [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ],
                model8:'',
                wid:'',
                cityList: [
                    {
                        value: 'New York',
                        label: 'New York'
                    },
                    {
                        value: 'London',
                        label: 'London'
                    },
                    {
                        value: 'Sydney',
                        label: 'Sydney'
                    },
                    {
                        value: 'Ottawa',
                        label: 'Ottawa'
                    },
                    {
                        value: 'Paris',
                        label: 'Paris'
                    },
                    {
                        value: 'Canberra',
                        label: 'Canberra'
                    }
                ],
            };
        },
        computed:{
            /*style(){
                return {
                    width:(this.wid+16)+'px'
                }
            }*/
        },
        methods: {

        }

    };
</script>

<style>
    .moreBtn .ivu-select-arrow{right: 1px;}
    .moreBtn .ivu-select-selection:hover,.moreBtn .ivu-select-selection-focused{border-color: #dcdee2;background-color: #eee}
    .moreBtn .ivu-select-visible .ivu-select-selection{border-color: #dcdee2;box-shadow:0 0 0 0}
</style>
<style scoped>
.moreBtn {position: relative}
.moreBtn .firBtn{position: absolute;left: 0;top: 0;z-index: 5}
</style>
