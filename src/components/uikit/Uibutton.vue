<template>
  <button class="ui-btn" @click="onClickBtn" :disabled=isDisabled
   :class="{
       'ui-btn-large':large,
       'ui-btn-xlarge':xlarge,
       'ui-btn-small':small,
       'ui-btn-xsmall':xsmall,
       'ui-btn-tile':tile,
       'ui-btn-rounded':rounded,
       'ui-btn-cricle':cricle,
       'ui-btn-disabled':isDisabled
   }"
   :style="!isDisabled?`background-color:${getColor}`:''"
   
  >
   <slot>Button</slot>
  </button>
</template>

<script lang="ts">
import { Vue, Component, Emit, Prop} from "vue-property-decorator";
//引入编写类样式组件所必须的类及装饰器;
// Uibutton.vue

@Component
export default class Uibutton extends Vue {
    // @Prop({type:Boolean,default:false})
    // large;
    @Prop(Boolean)
    private large: boolean |  undefined;
    @Prop(Boolean)
    private xlarge: boolean |  undefined;
    @Prop(Boolean)
    private small: boolean |  undefined;
    @Prop(Boolean)
    private xsmall: boolean |  undefined;
    @Prop(Boolean)
    private tile: boolean |  undefined;
    @Prop(Boolean)
    private rounded: boolean |  undefined;
    @Prop(Boolean)
    private cricle: boolean |  undefined;
    @Prop(Boolean)
    private isDisabled: boolean |  undefined;
    @Prop(String)
    private color: string |  undefined;
    //ts中类的变量需要进行初始化,解决办法可以设置类型为 或 undefined; 

    @Emit('click')
    private emitClickEvent(event: MouseEvent){
        console.log("111")
    }
    
    get getColor(){
        if(this.color){
            console.log(this.color);
            return this.color;
            
        }else{
            return  '#2D8CF0';
        }
    }
    
    private onClickBtn(event: MouseEvent){
        this.emitClickEvent(event);     
    }

    private mounted() {
        
    }
}
</script>

<style lang="less" scoped>
.baseStyle(@min-width,@height,@padding,@font){
    min-width: @min-width;
    height: @height;
    padding: 0 @padding;
    font-size: @font;
     &.ui-btn-rounded{
        border-radius: @height*0.5;
    }
    &.ui-btn-cricle{
        height: @min-width;
        border-radius: 50%;
        padding: 0;
    }
}
.ui-btn {
    .baseStyle(64px,36px,16px,0.875rem);
    border: 0 solid black;
    border-radius: 4px;
    outline: none;
    font-weight: 500;
    letter-spacing: 0.09em;
    //字符间距
    // background-color: var(bgColor);
    color: #17233D;
    cursor: pointer;
    user-select: none;
    &:hover{
        filter: brightness(110%);
    }
    //无法通过拖动,选中按钮中的文字
    &.ui-btn-large{
        .baseStyle(78px,44px,19px,0.875rem);
    }
    &.ui-btn-xlarge{     
        .baseStyle(92px,52px,23px,1rem);
    }
    &.ui-btn-small{
        .baseStyle(50px,28px,12px,0.75rem);
    }
    &.ui-btn-xsmall{
        .baseStyle(36px,20px,9px,0.625rem);
    }
    &.ui-btn-tile{
        border-radius: 0;
    }
    &.ui-btn-disabled{
        background-color: #cccccc;
        cursor: not-allowed;
        color: #fff;
    }
   
    
    //&为父类选择器 上方判断为true时,  按钮class会同时具有 .ui-btn .ui-btn-xlarge
}


</style>
