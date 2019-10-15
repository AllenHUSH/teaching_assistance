<template>
  <van-collapse v-model="activeNames">
    <van-collapse-item title="标题1" name="1">内容</van-collapse-item>
    <van-collapse-item title="标题2" name="2">内容</van-collapse-item>
    <van-collapse-item title="系统设置" name="3" icon="setting-o">
      <van-cell value="语言" is-link />
      <van-cell value="密码" is-link />
    </van-collapse-item>
  </van-collapse>
</template>
<script>
export default {
  data() {
    return {
      activeNames: ["1"]
    };
  }
};
</script>