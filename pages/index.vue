<template>
  <div class="m-8">
    <Video :slider-value="sliderValue" />
    <Slider @sliderValue="sliderValue = $event" @minMax="minMax = $event" />
  </div>
</template>

<script>
import Video from "~/components/Video.vue";
import Slider from "~/components/Slider.vue";

export default {
  components: {
    Video,
    Slider
  },
  data() {
    return {
      sliderValue: {},
      minMax: []
    };
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
