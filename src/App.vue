<template>
  <div id="app">
   <Home></Home>
  </div>
</template>

<script lang="ts">
import Home from '@/Home.vue';
import { Vue, Component } from "vue-property-decorator";//引入编写类样式组件所必须的类及装饰器;
@Component({
  components:{
    Home,
  }
})
export default class APP extends Vue {

}
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
