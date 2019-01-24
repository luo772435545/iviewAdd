<template>
    <div class="edit-box">
        <div class="look" v-if="iptStatus === 'look'">{{value[objKey]}}<Icon  @click="editStatus('edit')" class="icon" type="md-create" /></div>
        <div class="edit" v-if="iptStatus === 'edit'">
            <Input v-model="value[objKey]"
                   class="ipt"
                   :maxlength="maxlength"
                   :disabled="disabled"
                   :readonly="readonly"
                   :clearable="clearable"></Input><Icon @click="editStatus('look')" size="22" type="ios-checkmark" /><Icon @click="editStatus('close')" size="22" type="ios-close" />
        </div>
    </div>
</template>

<script>
    export default {
        name: 'editInput',
        props:{
            model:{
                type: Object
            },
            objKey:{
                type: String
            },
            status:{
                type: String,
                default:'look'
            } ,
            maxlength: {
                type: Number
            },
            disabled: {
                type: Boolean,
                default: false
            },
            readonly: {
                type: Boolean,
                default: false
            },
            clearable: {
                type: Boolean,
                default: false
            },
        },
        components: {},
        data () {
            return {
                data:JSON.parse(JSON.stringify(this.model)),
                iptStatus:this.status,
                resetIptStatus:'look',
            };
        },
        methods: {
            editStatus(status){
                let v = this;
                v.iptStatus = status;
                v.resetIptStatus = status;
                if(status === 'look'){
                    v.$emit('handleClick');
                }else if(status === 'close'){
                    v.value[v.objKey] = v.data[v.objKey];
                    v.iptStatus = 'look';
                }else {
                   v.data =  JSON.parse(JSON.stringify(v.model))
                }
            },
            handleInput(event){

            }
        },
        computed: {
            value :{
                get: function () {
                    let v = this;
                    if(v.resetIptStatus === 'close'){
                        return v.model
                    }else {
                        return v.model
                    }
                },
                set(){
                    let v = this;
                    return v.model
                }
            }
        }
    };
</script>

<style scoped>
    .edit-box{display: inline-block;}
    .look{line-height: 30px;}
    .look .icon{margin-bottom: 2px;vertical-align: text-top}
    .look:hover{border: 1px solid #ddd;padding-left: 5px;}
    .look ,.edit{display: inline-block;}
    .icon{padding-left: 100px;display: none;}
    .look:hover .icon{display: inline-block}
    .ipt{width: 300px;}
</style>
