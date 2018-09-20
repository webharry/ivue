# 详情模板页
<style>
.dome-alert .w-alert:not(:first-child){
  margin-top: 10px;
}
</style>
<script>
export default {
    data(){
        return {
            labels : [
                {
                    titles:['详情标题1','详情标题2'],
                    id:1,
                    colNum:{
                        col1:3,//第一列项数
                        col2:4//第二列项数
                    },
                    labelPosition:'top',//标签位置，四种：top,left,right,bottom
                    columns:2,//每行列数,两种：每行2列或每行3列
                    column:{
                        'name': {
                            label:'名字',
                            type:'text',
                            isShow:true,
                            style:'default'
                        },
                        'address': {
                            type:'link',
                            label:'地址',
                            isShow:true,
                            style:'default'
                        },
                        'more': {
                            type:'readMore',
                            label:'更多信息',
                            isShow:true,
                            style:'default'
                        },
                        'picture': {
                            type:'picture',
                            label:'图片1',
                            isShow:true,
                            style:'red'
                        }
                    }
                },
                {
                    titles:[],
                    id:2,
                    colNum:{
                        col1:2,//第一列项数
                        col2:3//第二列项数
                    },
                    labelPosition:'left',
                    columns:3,
                    column:{
                        'name': {
                            label:'名字',
                            type:'text',
                            isShow:true,
                            style:'default'
                        },
                        'address': {
                            type:'link',
                            label:'地址',
                            isShow:true,
                            style:'default'
                        },
                        'more': {
                            type:'readMore',
                            label:'更多信息',
                            isShow:true,
                            style:'default'
                        },
                        'picture': {
                            type:'picture',
                            label:'图片1',
                            isShow:true,
                            style:'default'
                        }
                    }
                }
            ],
            dataInfo:{
                "name": "ewww",
                "address": "http://wufazhuce.com/one/2202",
                "more": "ewww",
                "picture": "http://image.wufazhuce.com/FpExIypm6ZcwSpZMv3RrPitIHHSI"
            },
            labelPosition:"top"
        }
    },
    methods: {
        hello() {
            alert('Hello World!');
        }
    }
  }
</script>
# Alert 警告
----
用于页面中展示重要的提示信息。

### 基本用法
<div class="demo-block">
    <div v-for="item in labels">
        <xdetail :labels="item" :data="dataInfo" :colNum="item.colNum" :labelPosition="item.labelPosition" :columns="item.columns"></xdetail>
    </div>
</div>

```html
<template>
    <div v-for="item in labels">
        <xdetail :labels="item" :data="dataInfo" :colNum="item.colNum" :labelPosition="item.labelPosition" :columns="item.columns"></xdetail>
    </div>
</template>
<script>
export default {
    data(){
        return {
            labels : [
                {
                    titles:['详情标题1','详情标题2'],
                    id:1,
                    colNum:{
                        col1:3,//第一列项数
                        col2:4//第二列项数
                    },
                    labelPosition:'top',//标签位置，四种：top,left,right
                    columns:2,//每行列数,两种：每行2列或每行3列
                    column:{
                        'name': {
                            label:'名字',
                            type:'text',
                            isShow:true,
                            style:'default'
                        },
                        'address': {
                            type:'link',
                            label:'地址',
                            isShow:true,
                            style:'default'
                        },
                        'more': {
                            type:'readMore',
                            label:'更多信息',
                            isShow:true,
                            style:'default'
                        },
                        'picture': {
                            type:'picture',
                            label:'图片1',
                            isShow:true,
                            style:'red'
                        }
                    }
                },
                {
                    titles:[],
                    id:2,
                    colNum:{
                        col1:2,//第一列项数
                        col2:3//第二列项数
                    },
                    labelPosition:'left',
                    columns:3,
                    column:{
                        'name': {
                            label:'名字',
                            type:'text',
                            isShow:true,
                            style:'default'
                        },
                        'address': {
                            type:'link',
                            label:'地址',
                            isShow:true,
                            style:'default'
                        },
                        'more': {
                            type:'readMore',
                            label:'更多信息',
                            isShow:true,
                            style:'default'
                        },
                        'picture': {
                            type:'picture',
                            label:'图片1',
                            isShow:true,
                            style:'default'
                        }
                    }
                }
            ],
            dataInfo:{
                "name": "ewww",
                "address": "http://wufazhuce.com/one/2202",
                "more": "ewww",
                "picture": "http://image.wufazhuce.com/FpExIypm6ZcwSpZMv3RrPitIHHSI"
            },
            labelPosition:"top"
        }
    },
    methods: {
        hello() {
            alert('Hello World!');
        }
    }
  }
</script>
```

# API 

## detail props

| 属性 | 说明 | 类型 | 默认值 |
| --- | ---- | ---- | ------ |
| labels |  配置详情模板信息 | Array | [] |
| data |  详情数据集合  | Object | {} |
| labelPosition | 设置属性 labelPosition，可以改变表单域标签的位置，left 为左对齐，right 为右对齐，top 会置于表单域顶部 | String | top |
| columns |  label标签名称集合 | Object | {} |

## detail labels

| 属性 | 说明 | 类型 | 默认值 |
| --- | ---- | ---- | ------ |
| titles |  详情模板标题数组 | Array | [] |
| id |  模板配置参数id  | Number | -- |
| colNum | 列数对象，col1表示第一列项数，col2表示第二列项数 | Number | col1:1,col2:2 |
| labelPosition |  设置属性 labelPosition，可以改变表单域标签的位置，left 为左对齐，right 为右对齐，top 会置于表单域顶部 | String | top |
| columns |  每行列数,两种布局：每行2列或每行3列 | Number | 2 |
| column |  标签配置对象,键是标签参数，值是标签配置对象 | Object | {} |

## detail column
| 属性 | 说明 | 类型 | 默认值 |
| --- | ---- | ---- | ------ |
| label |  标签中文名称 | String | '' |
| type |  设置标签对应值渲染类型，一共四种：文本类型text，热链接类型link，查看更多dailog类型readMore,图片类型picture | String | -- |
| isShow |  控制标签隐藏显示，true展示，false不展示 | Boolean | true |
| style |  标签内容样式，两种：default为通用样式，red为加红色边框  | String | default |