<template>
    <div class="progress-box">
        <div class="progress" ref="progress"></div>
    </div>
</template>
<script>
export default {
    name: 'xProgress',
    props:{
        width:{
            type:String,
            default:'40%'
        }
    },
    data(){
        return {

        }
    },
    methods:{
        setProgress(){
            console.log(111,this.$refs.progress.style.width=this.width)
        }
    },
    mounted(){
        this.setProgress()
    }
}
</script>

<style lang="less" scoped>
.progress-box{
    width: 600px;
    height:30px;
    background-color:#ccc;
    .progress{
        height: 100%;
        background-color:blue;
    }
}
</style>

