<template>

    <div class="tabInputBox" @click="focusIn">
      <div class="tabInputList"
           v-for="(item,index) in tags"
           :key="index"
           v-if="tags.length>0"
           :title="item.attrVal">
          <span class="tabText">{{item.attrVal}}</span>
          <Icon type="md-close" @click="delTag(index)" class="tagClose"  size="14"></Icon>
      </div>
      <Input  class="tagInput"
              ref="tagIpt"
              placeholder="enter确定自定义关键词"
              :style="{width:tagName.length*12+100+'px'}"
              @on-enter="addTag"
              v-model.trim="tagName" />
    </div>
</template>

<script>

export default {
    name: 'tagInput',
    data () {
        return {
            tagName: ''
        };
    },
    props: {
        /**
         * @description 属性数组
         */
        tags: {
            type: Array
        }
    },
    methods: {
        focusIn () {
            this.$refs.tagIpt.focus();
        },
        delTag (index) {
            let v = this;
            v.tags.splice(index, 1);
            v.$emit('tagsMt', v.tags);
        },
        addTag () {
            let v = this;
            if (v.tagName !== '') {
                v.tags.push({attrVal: v.tagName});
                v.tagName = '';
                v.$emit('tagsMt', v.tags);
            }
        }
    }
};
</script>

<style>
  .tagInput .ivu-input{border: 0;}
  .tagInput .ivu-input:focus{box-shadow:0 0 0}
</style>
<style scoped>
    .tabInputList {
        margin: 3px 5px;
        border: 1px solid #ddd;
        padding: 2px 10px;
        background-color: #f3f3f3;
        display: inline-block;
        border-radius: 3px;
    }

    .tagClose {
        display: inline-block;
        font-size: 14px;
        margin-left: 10px;
        vertical-align: middle;
        cursor: pointer
    }

    .tabText {
        max-width: 260px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        vertical-align: middle;
        display: inline-block;
    }

    .tagClose:hover {
        color: #cc0031
    }

    .tabInputBox {
        border: 1px solid #ddd;
        border-radius: 4px;
        background-color: #fff;
        width: 100%;
        cursor: text
    }

    .tagInput {
        display: inline-block;
        max-width: 260px;
    }
</style>
