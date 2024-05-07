<script setup>
import {ref} from 'vue'
import TreeChart from './components/TreeChart.vue'
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
        content: '點擊email'
      },
      { 
        id: 3, 
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

</script>

<template>
  <header class="border">
    <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
  </header>
  <tree-chart class="mx-auto" :data="treeData[0]"/>

</template>

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
