<template>
    <div>
        <form>
            <Table ref="table" :columns="columns1" :data="data1" @on-selection-change="checkData"></Table>
        </form>
        <Button @click="validate">检查</Button>
        <Table :columns="columns1" :data="checkedData" ></Table>
        <Render></Render>
    </div>
</template>

<script>
    import AsyncValidator from 'async-validator';
    export default {
        name: 'uTable',
        data() {
            let v=this;
            return {
                validateState: '',
                validateMessage: '',
                visible:false,
                columns1: [
                    {
                        type: 'selection',
                        width: 60,
                        align: 'center'
                    },
                    {
                        title: 'Name',
                        key: 'name',
                        rules:{
                            name:[{
                                required: true,
                                message: '请填写用户名'
                            }]
                        },
                        render (h, params) {
                            let _this=this;
                            return  h('Input',{
                                class:(()=>{
                                    if(params.row.error&&params.row.error!=''){
                                        return  'validBor';
                                    }
                                })(),
                                props: {
                                    value: params.row.name
                                },
                                on: {
                                    input: function (event) {
                                        params.row.name=event;
                                        v.$nextTick(()=>{
                                            let arr = [];
                                            v.$refs.table.objData[params.index]._isChecked = false;
                                            var datas=v.$refs.table.objData;
                                            for ( let key in datas) {
                                                if(datas.hasOwnProperty(key) && datas[key]._isChecked){
                                                    arr.push(datas[key]);
                                                }
                                            }
                                            v.$refs.table.$emit('on-selection-change',arr);
                                            v.data1[params.index]=params.row;

                                        });
                                    },
                                    'on-blur':()=>{
                                        v.validMt(params.row,_this.column.rules);
                                    }
                                }
                            },[h('Tooltip',{
                                props:{
                                    trigger:'hover',
                                    content:params.row.error,
                                    transfer:true
                                },
                                slot:'suffix',
                            },[h('Icon',{
                                style:{
                                    color:'red',
                                    display:(()=>{
                                        if(params.row.error && params.row.error!=''){
                                            return  'block';
                                        }else {
                                            return 'none';
                                        }
                                    })()
                                },
                                props:{
                                    type:'md-information-circle',
                                    size:18
                                }
                            })])]);
                        }
                    },
                    {
                        title: 'Age',
                        key: 'age'
                    },
                    {
                        title: 'Address',
                        key: 'address'
                    }
                ],
                data1: [
                    {
                        name: '',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03',
                        error:''
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01',
                        error:''
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02',
                        error:''
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04',
                        error:''
                    }
                ],
                cc:false,
                checkedData:[],
            };
        },
        methods: {
            checkData(data){
                this.checkedData=data;
            },
            validate(){
                let v=this;
                const descriptor = this.columns1[1].rules;
                v.data1.forEach((item)=>{
                    v.validMt(item,descriptor);
                });
            },
            validMt(item,descriptor){
                const validator = new AsyncValidator(descriptor);
                validator.validate(item, (errors) => {
                    item.error = errors?errors[0].message:'';
                });
            }
        },
        computed: {

        }
    };
</script>

<style>
    .validBor input{border: 1px solid #ff0000}
    .validBor .ivu-input-icon{color: red}
</style>
<style scoped>

</style>
