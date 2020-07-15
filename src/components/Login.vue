<template>
  <div class="login_container">
    <div class="login_box">
      <!--图像区-->
      <div class="avatr_box">
        <img src="../assets/logo.png" alt />
      </div>
      <!--表单区-->
      <el-form ref="formRef" :rules="rules" :model="form" class="loginForm">
        <!--用户名区-->
        <el-form-item prop="name">
          <el-input placeholder="请输入用户名" prefix-icon="el-icon-user" v-model="form.name"></el-input>
        </el-form-item>
        <!--密码-->
        <el-form-item prop="password">
          <el-input placeholder="请输入密码" prefix-icon="el-icon-lock" v-model="form.password" show-password></el-input>
        </el-form-item>
        <!--按钮-->
        <el-form-item class="btns">
          <el-button type="primary" @click="login">登录</el-button>
          <el-button type="info" @click="resetFrom">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 表单数据绑定对象
      form: {
        name: 'admin',
        password: '123456'
      },
      rules: {
          name: [
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 3, max: 5, message: '用户名长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'change' },
             { min: 6, max: 10, message: '密码长度在 6 到 10 个字符', trigger: 'blur' }
          ],
      }
    };
  },
  methods:{
      resetFrom(){
          this.$refs.formRef.resetFields();
      },
      login(){
          this.$refs.formRef.validate(async valid=> {
              if(!valid){
                  return;
              }
              //const {data:res} = await this.$http.post('login', this.form);
              this.$message.success("成功");
              //this.$message.error("失败");
          });
      }
  }
};
</script>

<style lang="less" scoped>
.login_container {
  background: #2b4b6b;
  height: 100%;
}
.login_box {
  width: 450px;
  height: 300px;
  background: #fff;
  border-radius: 3px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  .avatr_box {
    height: 130px;
    width: 130px;
    border: 1ps solid #eee;
    border-radius: 50%;
    padding: 10px;
    box-shadow: 0 0 10px #ddd;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    img {
      height: 100%;
      width: 100%;
      border-radius: 50%;
      background: #eee;
    }
  }
  .btns {
    display: flex;
    justify-content: flex-end;
  }
  .loginForm{
      position: absolute;
      bottom: 0;
      width: 100%;
      padding: 0 20px;
      box-sizing: border-box;
  }
}
</style>