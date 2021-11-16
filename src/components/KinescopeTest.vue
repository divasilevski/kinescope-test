<script setup>
import { ref } from "vue";
import KinescopeList from "./KinescopeList.vue";

const rows = ref(2);
const cols = ref(2);
const autoPlay = ref(false);
const url = ref("https://kinescope.io/embed/200626438");

const count = ref(0);
const coulums = ref(2);

const handleRender = () => {
  count.value = rows.value * cols.value;
  coulums.value = cols.value;
};
const handleClear = () => {
  count.value = 0;
};
</script>

<template>
  <div class="app">
    <header>
      <input v-model="rows" type="number" placeholder="Кол-во строк" required />
      <input
        v-model="cols"
        type="number"
        placeholder="Кол-во колонок"
        required
      />
      <input v-model="url" type="text" placeholder="Ссылка на видео" required />
      autoPlay <input v-model="autoPlay" type="checkbox"/>
      <button @click="handleRender">Render</button>
      <button @click="handleClear">Clear</button>
    </header>

    <KinescopeList :count="count" :coulums="coulums" :url="url" :autoPlay="autoPlay" />
  </div>
</template>

<style>
.app {
}

.app header {
  margin-bottom: 30px;
}

.app .grid {
  display: grid;
}
</style>