# wecom-assistant 企微助手开发技术文档记录

## 技术栈
node版本: 16.17.1    
[vue3](https://cn.vuejs.org/) + [vite](https://cn.vitejs.dev/) + [electron](https://www.electronjs.org/zh/) + [ant-design-vue](https://www.antdv.com/components/overview-cn/)


## 插件
autoimport 自动引入插件  
unplugin-auto-import  
unplugin-vue-components 省去大量 import 语句  
```
// 自动引入插件属性
import AutoImport from 'unplugin-auto-import/vite'
// 按需引入antd
import ViteComponents from 'unplugin-vue-components/vite'
```

[pinia](https://pinia.vuejs.org/zh/index.html) 全局状态管理  
vue3-infinite-scroll-better 滚动加载优化  
```
v-infinite-scroll="getList"
:infinite-scroll-immediate-check="false"
:infinite-scroll-disabled="scrollDisabled"
:infinite-scroll-watch-disabled="scrollDisabled"
:infinite-scroll-distance="10"
```
图标使用svg封装，全局svg图标组件 
```
  <svg
    :class="['svg-icon', $attrs.class]"
    :style="{
      width: iconSize + 'px',
      height: iconSize + 'px',
      outline: 'none'
    }"
    aria-hidden="true"
  >
    <use :xlink:href="'#icon-' + iconName" :fill="color" />
  </svg>
```
全局less + scoped  
使用[lodash-es.js](https://blog.csdn.net/qq_45007419/article/details/124497061)工具函数  
[vuedraggable](https://www.itxst.com/vue-draggable/tutorial.html) 拖拽  
cloneDeep 深拷贝  
debounce 防抖  

## 代码风格
vue3使用setup函数写法  
使用ref()、unref()、reactive()写法  
钩子函数onMounted 、register  
使用const 定义变量和方法  
遍历使用filter+map+foreach  
父子传值 defineProps + emit()回调  
computed+watch  
箭头函数写法  
vue $attrs的使用

## electron
windows存放不同窗口界面  
控制不同窗口  
通信方式  
ipcRenderer 从渲染进程发送指令给主进程  
ipcMain 主页窗口命令  
new BrowserWindow 创建窗口并添加监听指令 

打开窗口时候，计算程序缩放比例  
窗口最大化、最小化minimize(),maximize(),unmaximize(),isMaximized()  
窗口退出、隐藏  
node全局进程
process.env.NODE_ENV
electronStorage 全局存储

electron热更新
electron增量更新、全局更新
多页面多窗口优化，窗口池、缓存池
