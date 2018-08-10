<template>
    <div>
        <div class="box" v-click-outside="handleClose">
            <p v-show="visible">这是一个测试例子23</p>
        </div>
        <Button>Default</Button>
    </div>
</template>
<script>
 import {directive as clickOutside} from 'v-click-outside-x';
export default {
    name: 'xalert',
    data() {
        return {
            visible: false,
        }
    },
    directives: { clickOutside },
    methods:{
        handleClose () {
            this.visible = !this.visible;
        },
    }
}
</script>
<style scoped>
.box{
    width:400px;
    height:200px;
    background: #ccc;
    margin:auto;
}
</style>


