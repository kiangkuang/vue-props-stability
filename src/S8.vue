<script setup lang="ts">
import { ref } from 'vue';
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
</script>

<template>
  <ul>
    <li>Allow multiple active items</li>
    <li>State stored independently</li>
    <li>State change handled by other element to avoid Scenario 3, 4, 5 issues</li>
    <li><b>Separate item and <code>is-active</code> props</b> similar to Scenario 2</li>
  </ul>

  <button
    v-for="n in 3"
    class="outline"
    @click="onClick(n)">
    Select {{ n }}
  </button>

  <Item
    v-for="item in list"
    :item="item"
    :is-active="selectedList.includes(item.id)"
  />
</template>
