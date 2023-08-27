<script setup lang="ts">
import { ref } from 'vue';
import Item from './Item.vue';

const list = ref([
  { id: 1 },
  { id: 2 },
  { id: 3 },
]);

const activeId = ref(1);

const onClick = (id: number) => activeId.value = id;
</script>

<template>
  <ul>
    <li><code>@click</code> on button to change active button</li>
    <li><code>@click</code> <a href="https://vuejs.org/guide/essentials/event-handling.html#calling-methods-in-inline-handlers">call method in inline handler</a></li>
    <li>Still an inline handler, so it is <b>redeclared every time</b> by render function and will be a treated as a prop change</li>
  </ul>

  <Item
    v-for="item in list"
    :id="item.id"
    :is-active="item.id === activeId"
    @click="onClick(item.id)"
  />
</template>
