<script setup lang="ts">
import { ref, computed } from 'vue';
import Item from './Item.vue';

const list = ref([
  { id: 1 },
  { id: 2 },
  { id: 3 },
]);

const selectedList = ref<number[]>([]);

const onClick = (n: number) => {
  const index = selectedList.value.indexOf(n);
  index >= 0
    ? selectedList.value.splice(index, 1)
    : selectedList.value.push(n)
}

const listWithState = computed(() => list.value.map(item => ({
  ...item,
  isActive: selectedList.value.includes(item.id),
})));
</script>

<template>
  <ul>
    <li>Allow multiple active items</li>
    <li>State stored independently</li>
    <li>State change handled by other element to avoid Scenario 3, 4, 5 issues</li>
    <li>Use <code>computed</code> to combine item and state into one object as props</li>
    <li>When state changes, <b>all computed objects are recreated</b> and treated as props change</li>
  </ul>

  <button
    v-for="n in 3"
    class="outline"
    @click="onClick(n)">
    Select {{ n }}
  </button>

  <Item
    v-for="item in listWithState"
    :item="item"
  />
</template>
