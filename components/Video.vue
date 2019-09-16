<template>
  <div class="">
    <video
      ref="video"
      src="~assets/video/cold.mp4"
      @click="playPause()"
    ></video>
    <p>{{ sliderValue }}</p>
  </div>
</template>
<script>
export default {
  components: {},
  props: {
    sliderValue: { type: Array, default: null }
  },
  data() {
    return {
      duration: 0
    };
  },
  computed: {
    sliderStart() {
      return this.sliderValue[0] / 100;
    },
    sliderEnd() {
      return this.sliderValue[1] / 100;
    },
    startSec() {
      return parseFloat(this.sliderStart * this.$refs.video.duration).toFixed(
        2
      );
    },
    endSec() {
      return parseFloat(this.sliderEnd * this.$refs.video.duration).toFixed(2);
    }
  },

  methods: {
    playPause: function() {
      if (this.$refs.video.paused === true) {
        this.$refs.video.play();
        this.$refs.video.currentTime = this.startSec;
      } else {
        this.$refs.video.pause();
        this.$refs.video.currentTime = this.startSec;
      }
    }
  }
};
</script>
