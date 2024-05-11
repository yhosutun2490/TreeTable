<template>
  <div class="flex-column w-[100%] h-[100dvh]">
    <header class="border">
    <h1 class="text-3xl font-bold underline">
    草稿
  </h1>
  </header>
  <div class="h-3/5">
    <tree-chart 
    class="mx-auto" :data="tree.root" 
    @getCurrentKey="(id)=>getCurrentKey(id)"
    />
  </div>
  <option-modal class="mt-auto flex space-x-[10px] p-5">
    <div 
      class="w-[100px] h-[100px] border flex items-center bg-slate-50"
      v-for="(item) in buttonOption"
      :key="item.id"
    >
      {{ item.content}}
    </div>
  </option-modal>
  <div>
    目前節點資料 id: {{ activeNodeKey }}
    <label for="">title</label>
    <input type="text" v-model="currentNodeData.value.title">
    <label for="">content</label>
    <input type="text" v-model="currentNodeData.value.content">
  </div>
</div>
</template>
<script setup>
import {ref,computed} from 'vue'
import TreeChart from './components/TreeChart.vue'
import OptionModal from './components/OptionModal.vue'
import {Tree} from './utility/Tree'
const tree = ref(new Tree(1, {
  title: '觸發事件',
  content: '點擊email'
}))
// 目前點擊節點的key
const activeNodeKey= ref(1)

tree.value.insert(1, 11, {
  title: '觸發事件',
  content: '點擊email'
});
tree.value.insert(11, 111, {
  title: '觸發事件',
  content: '點擊廣告'
});
tree.value.insert(1, 12, {
  title: '觸發事件',
  content: '點擊email'
});
tree.value.insert(12, 121, {
  title: '觸發事件',
  content: '點擊email'
});
tree.value.insert(12, 122, {
  title: '觸發事件123',
  content: '點擊email123'
});
tree.value.insert(12, 123, {
  title: '觸發事件123',
  content: '點擊email123'
});
function getCurrentKey(key) {
  activeNodeKey.value = Number(key)
  // 將該節點focus 增加active = true
  tree.value.activeNodeFocus(Number(key))
}
function addTreeNode() {
  tree.value.insert(11,111,{
    title: '觸發事件New',
    content: '點擊SMS'
  })
}
const currentNodeData = computed(()=>{
  return tree.value.find(activeNodeKey.value)
})



const buttonOption = ref([
  {
    id: 1,
    content:'傳送Email'
  },
  {
    id: 2,
    content:'傳送SMS'
  },
  {
    id: 3,
    content:'傳送Line'
  }
  ])
</script>


<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>import { data } from 'autoprefixer';

