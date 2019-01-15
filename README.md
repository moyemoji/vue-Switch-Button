# moyeSwitchButton
开关按钮vue组件

## 环境配置
```shell
npm install
npm run dev
http://localhost:8080/
```

## API
**wrapper_width**  定制开关按钮大小，Number，非必填项

**initial_state**  定制按钮初始开闭状态，Boolean，非必填项

**toggleBtn**      点击按钮返回按钮当前状态，返回值为arguments，Boolean


## 使用组件
```html
<template>
  <switch-button :wrapper_width="wrapper_width" :initial_state="initial_state" v-on:toggleBtn="showState(arguments)"></switch-button>
</template>
```
```js
import switchButton from '../src/switchButton/switch-button'; // 引入

data () {
  return {
    wrapper_width: 500, // 设置按钮大小
    initial_state: true, // 按钮初始开闭状态
    btnState: ''
  }
},
methods:{
  showState(val){ // 获取按钮当前状态
    console.log(val);
    this.btnState = val[0];
  }
}
```

## 预期效果
![有动态效果的开关按钮](http://wx2.sinaimg.cn/large/c4f30ad5gy1fz738ykc9rg20k20gd75r.gif)
