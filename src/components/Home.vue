<template>
  <div>
    <el-button type="info" @click="logOut">退出</el-button>
  </div>
</template>

<script>
export default {
  methods: {
    logOut() {
      // 清除token
      window.sessionStorage.clear();
      // 跳转到登录页
      this.$router.push("/login");
    }
  }
};
</script>

<style lang="less" scoped>
</style>