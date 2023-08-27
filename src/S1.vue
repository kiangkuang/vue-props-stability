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
    <li><code>active-id</code> pass into <code>&lt;Item&gt;</code> to let it calculate its own active state</li>
    <li>When <code>active-id</code> changes, <b>all</b> <code>&lt;Item&gt;</code> props will change</li>
  </ul>

  <input v-model="activeId" type="number" min="1" max="3">

  <Item
    v-for="item in list"
    :id="item.id"
    :active-id="activeId"
  />
</template>
