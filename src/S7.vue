<script setup lang="ts">
import { ref, watch } from 'vue';
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

const listWithState = ref(list.value.map(item => ({
  ...item,
  isActive: selectedList.value.includes(item.id),
})));

watch(selectedList, () => {
  // alternative: use array.splice to replace modified item in place
  listWithState.value.forEach(item => {
    if (item.isActive !== selectedList.value.includes(item.id)) {
      item.isActive = selectedList.value.includes(item.id);
    }
  });
}, { deep: true });
</script>

<template>
  <ul>
    <li>Allow multiple active items</li>
    <li>State stored independently</li>
    <li>State change handled by other element to avoid Scenario 3, 4, 5 issues</li>
    <li>Use <code>ref</code> to combine item and state into one object to use as props</li>
    <li>Use <code>watch</code> to <b>update state changes in place</b></li>
    <li>When state changes, <b>only some objects are recreated</b> and treated as props change</li>
  </ul>

  <button
    v-for="n in 3"
    class="outline"
    @click="onClick(n)">
    Select {{ n }}
  </button>

  <button class="outline secondary" @click="selectedList = []">Reset</button>

  <Item
    v-for="item in listWithState"
    :item="item"
  />
</template>
