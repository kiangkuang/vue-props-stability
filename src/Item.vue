<script setup lang="ts">
import { computed, onUpdated } from 'vue';

const props = defineProps<{
  id?: number,
  activeId?: number,
  isActive?: boolean,
  item?: any,
}>();

const active = computed(() => {
  if ((props.item?.id || props.id) === props.activeId) {
    return true;
  }
  return props.item?.isActive || props.isActive;
})

onUpdated(() => {
  console.log(new Date().toLocaleTimeString(), 'Updated', props.item?.id ?? props.id);
});
</script>

<template>
  <button :class="active ? 'primary' : 'secondary'">
    {{ item?.id || id }}
  </button>
</template>
