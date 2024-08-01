<template>
    <form @submit.prevent="submitLogin">
        <p>用户名：<input type="username" name="" id="" required="true"></p>
        <p>密&nbsp;&nbsp;&nbsp;码：<input type="password" required="true"></p>
        <p><span>验证码：<input type="text" name="" id="" class="Captcha" required="true"><img :src="captchaUrl" alt="验证码"><a href="#" class="unclear" @click.prevent="fetchCaptcha">看不清</a></span></p>
        <p><button type="submit">登录</button></p>
       </form>
   </template>
   
   <script>
   import axios from 'axios';
   
   export default{
       data(){
           return{
         username: '',
         password: '',
         captcha: '',
         captchaUrl: '',
           }
       },
       mounted() {
       this.fetchCaptcha();
     },
       methods:{
           fetchCaptcha() {
         this.captchaUrl = 'http://localhost:8080/api/captcha?' + new Date().getTime();
       },
           submitLogin(){
               const loginData ={
                   username : this.username,
                   password: this.password,
                   captcha: this.captcha
               }
   
           axios.post('http://localhost/api/adminlogin',loginData)
               .then(response =>{
                   alert(response.data)
               })
           .catch(error => {
               console.error('登录错误：',error)
           })
           }
       }
   }
   </script>
   
<style scoped>

</style>