<template>
  <div class="top"><img src="./assets/logo.png" alt=""></div>
  <p class="title">高校创新创业项目管理与学分认定系统</p>
 <div class="login">
  <p class="btn"><button :class="{active: role==='student'}" @click="setRole('student')">学生登录</button>
    <button :class="{active: role ==='teacher'}" @click="setRole('teacher')">教师登录</button>
    <button :class="{ active: role === 'administrator' }" @click="setRole('administrator')">管理员登录</button></p>
  <StudentLogin v-if="role==='student'"></StudentLogin>
  <TeacherLogin v-if="role==='teacher'"></TeacherLogin>
  <AdminLogin v-if="role==='administrator'"></AdminLogin>
 </div>
</template>

<script>
import StudentLogin  from './components/StudentLogin.vue';
import TeacherLogin from './components/TeacherLogin.vue';
import AdminLogin from './components/AdminLogin.vue';

export default {
  name: 'App',
  components: {
    StudentLogin,
    TeacherLogin,
    AdminLogin
  },
 


  methods: {
    setRole(role) {
      this.role=role
    },
},
data() {
    return {
      role:'student'
    };
  },
}
</script>

<style>
#app {
  display: flex;
  justify-content: center; /* 水平居中 */
  align-items: center; /* 垂直居中 */
  height: 100vh; /* 使父容器高度为视口高度 */
  flex-direction: column;
}
.top{
  width: 100%;
  height: 103px;
  background-color: brown;
  
}
.login{
height: 450px;
width: 500px;
border: 2px black solid;
margin: auto auto;
border-radius: 5px;
margin-top: 100px;
}
.btn button{
  width: 32%;
  height: 50px;
  background-color: brown;
  font-size: 20px;
  margin: 0 3px;
  border-radius: 5px;
  color: white;
}
button{
  font-family: 'Noto Sans SC', sans-serif; /* 修改字体为 Noto Sans SC */
}
.btn button:hover{
  box-shadow: inset 0 0 15px rgba(0, 123, 255, 0.7); /* 悬浮时的内阴影效果 */
}
.btn button:first-child{
  margin-left: 4px;
}

/* 激活状态的按钮样式 */
.btn button.active {
  background-color: darkred; /* 或者其他颜色 */
  border: 2px solid yellow; /* 添加边框来突出 */
}


form p{
  text-align: center;
  margin-top: 50px;
  font-size: 20px;
}
form p button{
  font-size: 20px;
  width: 200px;
  height: 60px;
  border-radius: 5px;
}
form p input{
  font-size:20px ;
}
.Captcha{
  width: 100px;
  
}
form p span img{
  border: 2px solid black;
  max-width: 100px;
  max-height: 30px;
  margin-left: 10px;

}
.top{
  position: absolute;
  top: 0px;
}
.top img{
  position: relative;
  top: 15px;
}
.unclear{
  margin-left: 10px;
}
form p button:hover{
  box-shadow: inset 0 0 15px rgba(0, 123, 255, 0.7); /* 悬浮时的内阴影效果 */
}
.title{
  font-size: 50px;
  margin-top: 300px;
  font-family: 'Noto Serif SC', serif; /* 修改字体为 Noto Serif SC */
}
</style>
