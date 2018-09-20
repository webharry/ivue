<template>
    <div>
        <div v-if="val.type === 'link'" :class="['span-line','tip',data[keyName]?'':'span-null-line']">
            <a :href="data[keyName]" target="_blank">{{data[keyName]}}</a>
        </div>
        <div v-if="val.type === 'text'" :class="['span-line',data[keyName]?'':'span-null-line',data[keyName+'redStyle']?'red':'']">
            {{data[keyName]}}
        </div>
        <div v-if="val.type === 'readMore'">
            <Button type="primary" @click="modal1 = true">查看更多</Button>
            <Modal
                v-model="modal1"
                title="Common Modal dialog box title"
                @on-ok="ok"
                @on-cancel="cancel">
                <p>Content of dialog</p>
                <p>Content of dialog</p>
                <p>Content of dialog</p>
            </Modal>
        </div>
        <div v-if="val.type === 'picture'">
            <div :class="['img-area',val.style === 'red'?'red-border':'']">
                <a :href="data[keyName]" target="_blank" :style="`background-image:url(${data[keyName]})`">
                </a>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'xrow',
    props:{
        data:{
            type:Object,
            default:() => {}
        },
        keyName:{
            type:String,
            default:''
        },
        val:{
            type:Object,
            default:() => {}
        }
    },
    data(){
        return {
            modal1: false
        }
    },
    methods: {
        ok () {
            this.$Message.info('Clicked ok');
        },
        cancel () {
            this.$Message.info('Clicked cancel');
        }
    }
}
</script>
<style lang="less" scoped>
.span-line{
    display: inline-block;
    width: 70%;
    padding: 0 5px;
    margin-right: 5px;
    white-space:normal;
    word-wrap: break-word;
    background-color: #eef1f6;
}
.span-null-line{
    height: 36px;
}
.tip{
    color:red;
}
.img-area {
    display:inline-block;
    width:100px;
    height:100px;
    overflow:hidden;
    border:solid 1px #fff;
    margin:2px 3px;
    a {
        display:block;
        height:100%;
        background-position:50% 50%;
        background-size:cover;
        transform:scale(1.0,1.0);
        transition-duration:0.5s;
        &:hover {
            transform:scale(1.1,1.1);
            transition-duration:0.5s;
        }
    }
    &:hover {
        border-color:#3ca0ff;
    }
}
.red{
    color:red;
}
.red-border{
    border:2px solid red;
}
</style>


