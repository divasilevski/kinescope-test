<template>
  <div class="kinescope-player">
    <div :id="'kinescope-' + videoId"></div>
  </div>
</template>

<script>
export default {
  props: {
    videoId: {
      type: [String, Number],
      default: "id",
    },
    kinescope: {
      type: String,
      default: "",
    },
    autoPlay: {
      type: Boolean,
      default: false,
    },
  },
  mounted() {
    if (window && window.Kinescope) {
      window.Kinescope.IframePlayer.create("kinescope-" + this.videoId, {
        url: this.kinescope,
        behaviour: {
          autoPlay: this.autoPlay,
          muted: true,
          autoPause: false,
        },
        ui: {
          header: false,
        },
      });
    }
  },
};
</script>

<style scoped>
.kinescope-player {
  width: 100%;
  height: 100%;
}
.kinescope-player :deep(iframe) {
  width: 100%;
  height: 100%;
}
</style>
