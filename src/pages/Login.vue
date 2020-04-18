<template>
  <div class="login">
    <div class="title">
      <h2>山野人家农产品店</h2>
      <!-- <h3>顾客端</h3> -->
    </div>
    <div class="container">
      <van-cell-group>
        <van-field
          class="input"
          v-model="user.username"
          required
          clearable
          label="用户名"
          placeholder="请输入用户名"
        />

        <van-field
          class="input"
          v-model="user.password"
          type="password"
          label="密码"
          placeholder="请输入密码"
          required
        />
      </van-cell-group>
    </div>
    <br>
    <div class="footer">
      <van-row>
      <van-col span="17" class="regist">
        <!-- <van-button size="small" type="info">注册</van-button> -->
      </van-col>
      <van-col span="5">
        <van-button size="small" type="danger" @click="loginHandler" style="background-color:#fff;color:#333;border:none">登录</van-button>
      </van-col>
    </van-row>
    </div>
  </div>
</template>
<script>
import { mapActions, mapState } from 'vuex';
export default {
  data(){
    return {
      user:{
        type:"customer"
      }
    }
  },
  methods: {
    ...mapActions("user",["login"]),
    loginHandler(){
      this.login(this.user)
      .then(()=>{
        this.$router.push({path:"/manager/home"})
        this.$toast({ message:"登录成功",duration: 700 });
      },(error)=>{
        this.$toast({ message:error,duration: 700 });
      })
    }
  }
}
</script>
<style scoped>
  .login{
    width: 100%;
    height: 100%;
    background-image: url("../assets/images/home.jpg");
    background-size:cover;
  }
  .title {
    color:#fff;
    text-align: center;
    padding-top: 200px;
  }
  .container {
    margin: 0 30px;
    color: #107515;
  }
  
  .footer {
    margin: 0 30px;
  }
  .regist {
    text-align: right;
    margin-right: 20px;
  }
  .input{
    width: 300px;
    background-color: none;
  }
</style>