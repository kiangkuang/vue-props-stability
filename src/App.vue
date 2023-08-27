<script setup lang="ts">
import { shallowRef } from 'vue';
import S1 from './S1.vue';
import S2 from './S2.vue';
import S3 from './S3.vue';
import S4 from './S4.vue';
import S5 from './S5.vue';
import S6 from './S6.vue';
import S7 from './S7.vue';
import S8 from './S8.vue';

const list = shallowRef([
  { component: S1, title: 'Scenario 1 - active-id prop' },
  { component: S2, title: 'Scenario 2 - is-active prop' },
  { component: S3, title: 'Scenario 3 - @click inline handler' },
  { component: S4, title: 'Scenario 4 - @click call method in inline handler' },
  { component: S5, title: 'Scenario 5 - @click method handler' },
  { component: S6, title: 'Scenario 6 - Computed object prop' },
  { component: S7, title: 'Scenario 7 - Modify object in place' },
  { component: S8, title: 'Scenario 8 - Separate item and is-active props' },
]);

const selected = shallowRef(list.value[0]);

const onChange = () => {
  console.clear();
  console.log(selected.value.title);
};
onChange();
</script>

<template>
  <main>
    <select v-model="selected" @change="onChange">
      <option v-for="item in list" :value="item">
        {{ item.title }}
      </option>
    </select>

    <article>
      <component :is="selected.component"/>

      <a href="https://github.com/kiangkuang/vue-props-stability" target="_blank">
        <img src="./qr.png">
      </a>
    </article>
  </main>
</template>

<style lang="scss">
$semantic-root-element: "#app";
@import "@picocss/pico/scss/pico";

#app > main {
  padding: 0;
}

article {
  margin: 0;
  padding: var(--block-spacing-horizontal);
}

img {
  display: block;
  width: 50%;
  margin: 0 auto;
  border-radius: 5%;
  background-color: white;
  box-shadow: var(--card-box-shadow);
}
</style>
