<script setup lang="ts">
import { ref } from 'vue';
import Item from './Item.vue';

const list = ref([
  { id: 1, onClick: () => activeId.value = 1 },
  { id: 2, onClick: () => activeId.value = 2 },
  { id: 3, onClick: () => activeId.value = 3 },
]);

const activeId = ref(1);
</script>

<template>
  <ul>
    <li><code>@click</code> on button to change active button</li>
    <li><code>@click</code> is <a href="https://vuejs.org/guide/essentials/event-handling.html#method-handlers">method handler</a></li>
    <li>Event handler function <b>comes from <code>script</code> and can be cached</b></li>
  </ul>

  <Item
    v-for="item in list"
    :id="item.id"
    :is-active="item.id === activeId"
    @click="item.onClick"
  />
</template>
