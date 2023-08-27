<script setup lang="ts">
import { ref } from 'vue';
import Item from './Item.vue';

const list = ref([
  { id: 1 },
  { id: 2 },
  { id: 3 },
]);

const activeId = ref(1);
</script>

<template>
  <ul>
    <li><code>@click</code> on button to change active button</li>
    <li><code>@click</code> is <a href="https://vuejs.org/guide/essentials/event-handling.html#inline-handlers">inline handler</a></li>
    <li>Inline handler is <b>redeclared every time</b> by render function and will be a treated as a prop change</li>
  </ul>

  <Item
    v-for="item in list"
    :id="item.id"
    :is-active="item.id === activeId"
    @click="activeId = item.id"
  />
</template>
