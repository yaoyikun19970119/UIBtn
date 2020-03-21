<template>
  <div class="root-home">
    <div class="btn-container">
      <Uibutton   
        @click="onClick"
        :large="large"
        :xlarge="xlarge"
        :xsmall="xsmall"
        :small="small"
        :tile="tile"
        :rounded="rounded"
        :cricle="cricle"
        :isDisabled="isDisabled"
        color='red'
      >hello</Uibutton>
    </div>
    <div class="btn-group">
      <Uibutton class="btn" @click="resize('xsmall')">超小</Uibutton>
      <Uibutton class="btn" @click="resize('small')">小</Uibutton>
      <Uibutton class="btn" @click="resize('normal')">正常</Uibutton>
      <Uibutton class="btn" @click="resize('large')">大</Uibutton>
      <Uibutton class="btn" @click="resize('xlarge')">超大</Uibutton>
    </div>
    <div class="btn-group">
      <Uibutton class="btn" @click="changeRadius('tile')">矩形</Uibutton>
      <Uibutton class="btn" @click="changeRadius('normal')">正常</Uibutton>
      <Uibutton class="btn" @click="changeRadius('rounded')">半圆</Uibutton>
      <Uibutton class="btn" @click="changeRadius('cricle')">圆型</Uibutton>
    </div>
    <div class="btn-group">
      <Uibutton class="btn" @click="changeDisable()">禁用</Uibutton>
    </div>
  </div>
</template>

<script lang="ts">
import Uibutton from "@/components/uikit/Uibutton.vue";

import { Vue, Component } from "vue-property-decorator";
//引入编写类样式组件所必须的类及装饰器;

// Home.vue
@Component({
  components: {
    Uibutton
  }
})
export default class Home extends Vue {
  private large: boolean = false;
  private xlarge: boolean = false;
  private small: boolean = false;
  private xsmall: boolean = false;
  private tile: boolean = false;
  private rounded: boolean = false;
  private cricle: boolean = false;
  private isDisabled: boolean = false;

  private resize(name: string) {
    switch (name) {
      case "xsmall":
        this.large = false;
        this.xsmall = true;
        this.small = false;
        this.xlarge = false;
        break;
      case "small":
        this.large = false;
        this.xsmall = false;
        this.small = true;
        this.xlarge = false;
        break;
      case "normal":
        this.large = false;
        this.xsmall = false;
        this.small = false;
        this.xlarge = false;
        break;
      case "large":
        this.large = true;
        this.xsmall = false;
        this.small = false;
        this.xlarge = false;
        break;
      case "xlarge":
        this.large = false;
        this.xsmall = false;
        this.small = false;
        this.xlarge = true;
        break;
    }
  }

  private changeRadius(name: string) {
    switch (name) {
      case "tile":
        this.tile = true;
        this.rounded = false;
        this.cricle = false;
        break;
      case "normal":
        this.tile = false;
        this.rounded = false;
        this.cricle = false;
        break;
      case "rounded":
        this.tile = false;
        this.rounded = true;
        this.cricle = false;
        break;
      case "cricle":
        this.tile = false;
        this.rounded = false;
        this.cricle = true;
        break;
    }
  }

  private changeDisable(){
      console.log("111");
      this.isDisabled=!this.isDisabled;
  }

  private onClick(event: MouseEvent) {
    console.log(event);
  }
}
</script>

<style lang="less" scope>
.btn-container {
  width: 480px;
  height: 160px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.btn-group {
  .btn {
    margin: 6px;
  }
}
</style>
