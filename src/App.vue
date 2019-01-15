<template>
  <div id="app">
    <switch-button :wrapper_width="wrapper_width" :initial_state="initial_state" v-on:toggleBtn="showState(arguments)"></switch-button>
    <div>
      <!-- <span>当前开关状态为：{{btnState}}</span> -->
    </div>
  </div>
</template>


<script>
import switchButton from '../src/switchButton/switch-button'; // 引入

/*
  父组件——>switch-button：
  wrapper_width：按钮的宽度
  initial_state：按钮初始开启状态

  switch-button——>父组件
  toggleBtn：切换按钮时传回按钮状态，true表示开启，false表示关闭
*/

export default {
  name: 'app',
  data () {
    return {
      wrapper_width: 200,
      initial_state: true,
      btnState: ''
    }
  },
  components:{ //注册插件
    switchButton
  },
  methods:{
    showState(val){
      console.log(val);
      this.btnState = val[0];
    }
  }
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
