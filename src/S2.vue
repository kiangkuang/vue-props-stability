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
    <li><code>is-active</code> props to set <code>&lt;Item&gt;</code> state</li>
    <li>When active item changes, <b>only some</b> <code>&lt;Item&gt;</code> props will change</li>
  </ul>

  <input v-model="activeId" type="number" min="1" max="3">

  <Item
    v-for="item in list"
    :id="item.id"
    :is-active="item.id === activeId"
  />
</template>
