<template>
  <div class="flex-column w-[100%] h-[100dvh]">
    <header class="border">
    <h1 class="text-3xl font-bold underline">
    草稿
  </h1>
  </header>
  <div class="h-3/5">
    <tree-chart class="mx-auto" :data="treeData[0]"/>
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
</div>


</template>
<script setup>
import {ref} from 'vue'
import TreeChart from './components/TreeChart.vue'
import OptionModal from './components/OptionModal.vue'
const treeData = ref([
  {
    id: 1, 
    title: '觸發事件',
    content: '點擊email',
    children: [
      { 
        id: 1, 
        title: '觸發事件',
        content: '點擊email'
      },
      { 
        id: 2, 
        title: '觸發事件',
        content: '點擊email',
        children: [
          { 
            id: 1, 
            title: '觸發事件',
            content: '點擊email',
            children: [
            { 
              id: 5, 
              title: '觸發事件',
              content: '點擊email'
            }

            ]
          },
          { 
            id: 2, 
            title: '觸發事件',
            content: '點擊email',
            children: [
            { 
              id: 5, 
              title: '觸發事件',
              content: '點擊email'
            },
            { 
              id: 5, 
              title: '觸發事件',
              content: '點擊email'
            }]
          },
        ]
        
      },
      { 
        id: 3, 
        title: '觸發事件',
        content: '點擊email',
        children: [
          { 
            id: 1, 
            title: '觸發事件',
            content: '點擊email',
            children: [
            { 
              id: 5, 
              title: '觸發事件',
              content: '點擊email'
            }

            ]
          },
          { 
            id: 2, 
            title: '觸發事件',
            content: '點擊email'
          },
        ]
      }
  ]
  },
  {
    id: 2, 
    title: '觸發事件',
    content: '點擊email'
  },
  {
    id: 3, 
    title: '觸發事件',
    content: '點擊email'
  }
])
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
</style>
