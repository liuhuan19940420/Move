<template>
  <div class="mine">
   <div class="conent">
  <img src="../assets/images/5denglujiemian/denglujiemian_1.png" alt="">
  <div class="name"><span></span> <input type="text" v-model="input.username"  placeholder="输入手机号"></div>
  <div class="pwd"><span></span> <input type="text"  v-model="input.password" placeholder="输入密码"></div>
  <button @click="onSubmit">登&nbsp;&nbsp;&nbsp;录</button>
   <p><span></span>&nbsp; &nbsp;&nbsp;第三方登录&nbsp;&nbsp; &nbsp;<span></span></p>
   <div class="icon"><span></span><span></span><span></span></div>
</div>
<div class="foot">
 <a href="#">忘记密码</a>
 &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; |  &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;  
 <router-link :to="{path:'/reg/'}" >立即注册</router-link>
</div>
<!--  <video src="../assets/videoviewdemo.mp4" autoplay="autoplat" controls="controls"></video>
 <audio src="../assets/pfzl.mp3"  autoplay="autoplat" controls="controls"></audio> -->
  </div>
</template>

<script>
import Vue from 'vue'
import Axios from 'axios'
Vue.prototype.$axios = Axios;
import qs from "qs"
export default {
  name: 'mine',
  data () {
    return {
     input:{
      username:"",
      password:"",
      reusername:"",
      repassword:""
     }
    }
  },
   methods:{
  onSubmit(event){
     /*this.$axios.post("http://localhost:3000/login",qs.stringify*/
     this.$axios.get("./static/myjson.json",qs.stringify(
      {
        username:this.input.username,
        password:this.input.password



      }))
      .then(res => {
       console.log(this.input.password)
       console.log(res.data)
        if(res.data.length>0){
           if(res.data[0].user[0].user1[0].upwd==this.input.password||res.data[0].user[0].user2[0].upwd==this.input.password||
           res.data[0].user[0].user3[0].upwd==this.input.password||res.data[0].user[0].user4[0].upwd==this.input.password){

             setTimeout('window.location="http://127.0.0.1:8080/#/yundong"',60)
         /* this.nick = res.data[0].username;*/
           }else{
          alert("登陆失败,");
        }
       }else{
          alert("登陆失败,用户名或密码错误")
        }
      })
      .catch(error => {
        console.log(error);
      })
    }

  },
   components:{
      
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.mine{
  background-color: #895EEC;
  height: 667/50rem;
  overflow: hidden;
  .conent{
    border-radius: 2/50rem;
    width:314/50rem;
    height: 463/50rem; 
    background-color: #fff;
    margin: 77/50rem auto 43/50rem ;
    img{
      height: 93/50rem;
      width: 93/50rem;
      margin-top: 45/50rem;
    }
    .name{
      text-align: center;
      position: relative;
      margin-left: 15/50rem;
      margin-top: 20/50rem;

      span{
        display: inline-block;
        height: 30/50rem;
        width: 30/50rem;
        background: url("../assets/images/5denglujiemian/denglujiemian_2.png") no-repeat;
        background-size: 20/50rem 20/50rem;
        position: absolute;
        top: 5/50rem;
        left:51/50rem;
      }
      input{
        width:150/50rem; 
        height: 24/50rem;
        border: none;
        border-bottom: 1px solid #D6D6D6;

      }

    }
    .pwd{
      position: relative;
      margin-left: 15px;

      span{
        display: inline-block;
        height: 30/50rem;
        width: 30/50rem;
        background: url("../assets/images/5denglujiemian/denglujiemian_3.png") no-repeat;
        background-size: 20/50rem 20/50rem;
        position: absolute;
        top: 6/50rem;
        left:51/50rem;
      }
      input{
        position: absolute;
        top:0px;
        left:80/50rem;
        width:150/50rem; 
        height: 24/50rem;
        border: none;
        border-bottom: 1px solid #D6D6D6;
      }
    }
    button{
      width: 270/50rem;
      height: 44/50rem;
      margin-top: 60/50rem;
      border-radius:22rem; 
      background-color: #AB8AF3;
      border:none;
      color: #fff;
      font-size: 20/50rem;

    }
    p{
      margin-top: 50/50rem;
      font-size: 12/50rem;
      color: #C6C6C6;
      span{
        display: inline-block;
        width: 80/50rem;
        border-top: 1px solid #C6C6C6;
        position: relative;
        top: -4/50rem;
      }
    }
    .icon{
      text-align: center;
      margin-top: 20/50rem;
      span{
        display: inline-block;
        width: 24/50rem;
        height: 22/50rem;
       &:nth-child(2){
        margin:0 40/50rem;
        background: url("../assets/images/5denglujiemian/denglujiemian_4.png") no-repeat;
        background-size: 24/50rem 22/50rem;
       }
       &:nth-child(1){
        background: url("../assets/images/5denglujiemian/denglujiemian_5.png") no-repeat;
        background-size: 26/50rem 22/50rem;
       }
       &:nth-child(3){
        background: url("../assets/images/5denglujiemian/denglujiemian_6.png") no-repeat;
        background-size: 24/50rem 22/50rem;
       }
      }
    }
    
  }
  .foot{
    font-size: 15/50rem;
      color: #fff;
    
    a{
      color: #fff;
      text-decoration: none;
    }
  }

}


</style>
