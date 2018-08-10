<script>
 export default {
    data(){
        return {
            msg:'hello'
        }
    }
  }
</script>
# Filters 过滤器
----
用于页面中展示重要的提示信息。

### 基本用法
```html
<template>
  <div>
    {{msg | date}}
  </div>
</template>
```
```js
<script>
 export default {
    data(){
        return {
            msg:'hello'
        }
    }
  }
</script>
```
<div class="dome-alert demo-block">
  {{msg | date}}
</div>