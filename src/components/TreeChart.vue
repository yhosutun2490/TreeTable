<template>
 <table class="w-[100%] h-[100%]">
  <!--主要父元素-->
  <tr class="flex justify-center  w-[100%]">
    <td colspan=8 class="parent relative flex justify-center">
      <div 
      class="card w-[100px] h-[100px] bg-blue bg-slate-50 hover:cursor-pointer"
      @click="($event)=>blockOnfocus($event)"
      @mouseleave.self="($event)=>removeFocus($event)"
      >
        <div class="header">{{ props.data.title }}</div>
        <div class="body">{{ props.data.content}}</div>
        <div class="footer">按鈕</div>
      </div>
    </td>
  </tr>
  <!--子元素-->
  <tr class="flex justify-around mt-[45px] w-[100%]" v-if="props.data.children">
    <td class="child relative w-[100%] flex justify-center"  v-for="item in props.data.children" :key="item.id">
      <TreeChart
      :data="item"
      v-if="item.title"
      />
    </td>
  </tr>
 </table>
</template>
<script setup>
import {defineProps } from 'vue'
import TreeChart from './TreeChart.vue'
const props = defineProps({
  data: {
    type: Object,
    default: ()=>{}
  }
})
function blockOnfocus(e) {
  if (Array.from(e.target.classList).includes('card')) {
    e.target.classList.add('focus-animate')
  } else {
    e.target.parentNode.classList.add('focus-animate')
  }
}
function removeFocus(e) {
  e.target.classList.remove('focus-animate')
}
console.log("props",props)
</script>

<style scoped>
.parent::after{
  content: '';
  position: absolute;
  left: 50%;
  bottom: -25px;
  height: 30px;
  border-left: 2px dashed rgb(159, 186, 202);
  transform: translate3d(-1px, 0, 0);

}
.child:last-child:before,
.child:first-child:before {
  display: none;
}
.child::before {
  content: '';
  position: absolute;
  left: 50%;
  bottom: 100%;
  height: 15px;
  border-left: 2px dashed rgb(159,186,202);
  transform: translate3d(-1px,0,0);
}
.child::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  top: -15px;
  border-top: 2px dashed rgb(159,186,202);
}
/* 前後第一個和最後一個元素橫線修飾蓋掉 */
.child:first-child::after {
  left: 50%;
  height: 15px;
  border: 2px dashed;
  border-color: rgb(159,186,202) transparent transparent rgb(159,186,202);
  border-radius: 6px 0 0 0;
  transform: translate3d(1px,0,0);
}
.child:last-child::after {
  right: 50%;
  height: 15px;
  border: 2px dashed;
  border-color: rgb(159,186,202) rgb(159,186,202) transparent transparent;
  border-radius: 0 6px 0 0;
  transform: translate3d(1px,0,0);
}
.focus-animate {
  border: 2px solid gold;

}
</style>