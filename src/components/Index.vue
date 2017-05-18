<template>
  <div id="header">
    <common-header></common-header>
    <common-content @showDialog="showDialog" :logined='logined'></common-content>
    <v-dialog v-show='show'>
      <div slot='title'>登陆</div>
      <div slot='body'>
        用户名：<input type="text" v-model='username'><br/>
        密码：<input type="password" v-model='password'><br/>
        <button @click='login'>确认</button>
      </div>
    </v-dialog>    
  </div>
</template>

<script>
import CommonHeader from './CommonHeader'
import CommonContent from './CommonContent'
import VDialog from './Dialog'

import Axios from 'axios'
export default {
  name: 'hello',
  data () {
    return {
      // msg: 'Welcome to Your Vue.js App'
      show:false,
      username:'',
      password:'',
      logined:false
    }
  },
  components:{ CommonHeader,CommonContent,VDialog },
  methods:{
    showDialog:function(data){
      this.show = true;
    },
    login:function(){
      // alert(this.username + '' + this.password);
      // 调用登陆接口
        var params = new URLSearchParams();
        params.append('username',this.username);
        params.append('password',this.password);
        Axios.post('http://127.0.0.1/eshop/welcome/login',params).then((res)=>{
          if(res.data == 'success'){
            this.show = false;
            this.logined = true;
          }
        }); 
        //this.show = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
