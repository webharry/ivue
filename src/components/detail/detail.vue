<template>
    <div class="box">
        <Menu v-if="labels.titles&&labels.titles.length" mode="horizontal" :theme="theme1" active-name="1">
            <MenuItem v-for="(title,index) in labels.titles" :name="index">
                <!-- <Icon type="ios-paper" /> -->
                {{title}}
            </MenuItem>
        </Menu>
        <br>
        <div v-if="inline">
            <Row :gutter="16">
                <Col :xs="2" :sm="4" :md="6" :lg="8">Col</Col>
                <Col :xs="20" :sm="16" :md="12" :lg="8">Col</Col>
                <Col :xs="2" :sm="4" :md="6" :lg="8">Col</Col>
            </Row>
        </div>
        <div v-if="!inline">
            <Row v-if="columns === 2" :gutter="16">
                <Col :xs="12" :sm="12" :md="12" :lg="12">
                    <Form :label-position="labelPosition">
                        <FormItem v-for="(val, key, index) in labels.column" v-if="index < colNum.col1" :key="index" :label="val.label+':'">
                            <xrow :val="val" :keyName="key" :data="data"></xrow>
                        </FormItem>
                    </Form>
                </Col>
                <Col :xs="12" :sm="12" :md="12" :lg="12">
                    <Form :label-position="labelPosition">
                        <FormItem v-for="(val, key, index) in labels.column" v-if="index >= colNum.col1" :key="index" :label="val.label+':'">
                            <xrow :val="val" :keyName="key" :data="data"></xrow>
                        </FormItem>
                    </Form>
                </Col>
            </Row>
            <Row v-if="columns === 3" :gutter="16">
                <Col :xs="8" :sm="8" :md="8" :lg="8">
                    <Form :label-position="labelPosition">
                        <FormItem v-for="(val, key, index) in labels.column" v-if="index < colNum.col1" :key="index" :label="val.label+':'">
                            <xrow :val="val" :keyName="key" :data="data"></xrow>
                        </FormItem>
                    </Form>
                </Col>
                <Col :xs="8" :sm="8" :md="8" :lg="8">
                    <Form :label-position="labelPosition">
                        <FormItem v-for="(val, key, index) in labels.column" v-if="index >= colNum.col1 && index < colNum.col2" :key="index" :label="val.label+':'">
                            <xrow :val="val" :keyName="key" :data="data"></xrow>
                        </FormItem>
                    </Form>
                </Col>
                <Col :xs="8" :sm="8" :md="8" :lg="8">
                    <Form :label-position="labelPosition">
                        <FormItem v-for="(val, key, index) in labels.column" v-if="index >= colNum.col2" :key="index" :label="val.label+':'">
                            <xrow :val="val" :keyName="key" :data="data"></xrow>
                        </FormItem>
                    </Form>
                </Col>
            </Row>
        </div>
    </div>
</template>
<script>
import xrow from './xrow'
export default {
    name:'xdetail',
    props:{
        inline:{
            type:Boolean,
            default:false
        },
        labels:{
            type:Object,
            default: () => {}
        },
        data:{
            type:Object,
            default:() => {}
        },
        history:{
            type:Array,
            default:() => []
        },
        colNum:{//控制每列条数
            type:Object,
            default: () => {
                col1 = 1 //第一列项数
                col2 = 2 //第二列项数
            }
        },
        labelPosition:{
            type:String,
            default:"top"
        },
        columns:{
            type:Number,
            default:2
        }
    },
    data(){
        return {
            theme1:'light'
        }
    },
    components:{
        xrow
    }
}
</script>
<style scoped lang="less">
.list-area {
    padding: 5px;
    border: 1px solid #ccc;
}
.el-menu-demo{
    margin-bottom: 8px;
}
.title{
    font-size: 20px;
    float:left;
    margin-right: 15px;
    padding-left: 4px;
}
</style>


