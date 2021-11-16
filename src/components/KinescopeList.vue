
<script>
import Kinescope from "./Kinescope.vue";
export default {
  components: {
    Kinescope,
  },
  props: ["coulums", "count", "url", "autoPlay"],
};
</script>

<template>
  <div class="grid" :style="`grid-template-columns: repeat(${coulums}, 1fr);`">
    <Kinescope
      v-for="(id, index) in count"
      :key="index + Date.now()"
      :videoId="index + Date.now()"
      :kinescope="url"
      :autoPlay="autoPlay"
    />
  </div>
</template>

<style>
.grid {
  display: grid;
}
</style>