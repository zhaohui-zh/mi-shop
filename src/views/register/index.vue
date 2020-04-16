<template>
  <div class="app-init pay-page scroll-box">
    <header-back title="注册"></header-back>
    <div class="padding-box" align="center">
      <div class="img-padding-box">
        <el-image :src="src" :fit="fit"></el-image>
      </div>
      <el-card class="form-container" shadow="never">
        <el-form v-loading="loading" element-loading-text="拼命加载中">
          <el-form-item label="手机号：">
            <el-input placeholder="请输入手机号" v-model="telphone"></el-input>
          </el-form-item>
          <el-form-item label="密码：">
            <el-input placeholder="请输入密码" v-model="password" show-password></el-input>
          </el-form-item>
          <el-form-item label="密码：">
            <el-input placeholder="请确认密码" v-model="password" show-password></el-input>
          </el-form-item>
          <el-form-item label="验证码：">
            <el-input placeholder="请输入验证码" v-model="password" show-password></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="getCode" plain>获取验证码</el-button>
            <el-button type="primary" @click="onRegister" plain>确认注册</el-button>
          </el-form-item>
        </el-form>
      </el-card>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import headerBack from "../../components/header-back";
import md5 from "js-md5";

export default {
  name: "register",
  components: {
    headerBack
  },
  data() {
    return {
      src:
        "https://account.xiaomi.com/static/res/11eb7d1/account-static/respassport/acc-2014/img/2018/milogo@2x.png",
      fit: "contain",
      telphone: "",
      password: "",
      loading: false
    };
  },
  methods: {
    onRegister: function() {
      let salt = "@V90sd~~|czx59450)#gg";
      let pwd = md5(salt + this.password);
      // alert(pwd);
      this.loading = true;
      let that = this;
      this.sleep(3000).then(function() {
        that.loading = false;
        that.$message({
          showClose: true,
          message: "注册成功",
          type: "success"
        });
        that.$router.openPage('/mine');
      }); 
    },
    getCode: function() {
      // alert("验证码已发送，请注意查收");
      this.loading = true;
      let that = this;
      this.sleep(3000).then(function() {
        that.loading = false;
        that.$message({
          showClose: true,
          message: "验证码发送成功",
          type: "success"
        });
      });
    },
    sleep: function(delay) {
      return new Promise(function(resolve, reject) {
        setTimeout(resolve, delay);
      });
    }
  }
};
</script>

<style type="text/sass" lang="sass">
.pay-page
  background-color: #fff
  .padding-box
    padding: 0.4rem
    color: #333
    .color
      color: orange
      ul
        padding-left: 0.8rem
      li
        list-style: disc
    .img-padding-box
      margin: 0.5rem
</style>
