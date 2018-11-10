<style>
.dome-alert .w-alert:not(:first-child){
  margin-top: 10px;
}
</style>
<script>
 export default {
    methods: {
      hello() {
        alert('Hello World!');
      }
    }
  }
</script>
# progress 进度条
----
用于页面中展示重要的提示信息。

### 基本用法
<div class="dome-alert demo-block">
  <xProgress width="10%"></xProgress>
</div>
