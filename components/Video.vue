<template>
  <div class="">
    <video
      ref="video"
      src="~assets/video/cold.mp4"
      @click="playPause()"
      @timeupdate="time()"
      @ended="ended()"
    ></video>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    sliderValue: { type: Object, default: null }
  },
  data() {
    return {
      duration: 0
    };
  },
  computed: {
    startSec() {
      return parseFloat(
        this.sliderValue.start * this.$refs.video.duration
      ).toFixed(2);
    },
    endSec() {
      return parseFloat(
        this.sliderValue.end * this.$refs.video.duration
      ).toFixed(2);
    }
  },
  watch: {
    sliderValue: function(value, oldvalue) {
      this.$refs.video.pause();
      if (value.start !== oldvalue.start) {
        this.$refs.video.currentTime = this.startSec;
        return;
      }
      if (value.end !== oldvalue.end) {
        this.$refs.video.currentTime = this.endSec;
      }
    }
  },
  methods: {
    playPause: function() {
      if (this.$refs.video.paused === true) {
        if (this.$refs.video.currentTime >= this.endSec) {
          this.$refs.video.currentTime = this.startSec;
        }
        if (this.$refs.video.currentTime < this.startSec) {
          this.$refs.video.currentTime = this.startSec;
        }
        this.$refs.video.play();
      } else {
        this.$refs.video.pause();
      }
    },
    time() {
      if (this.$refs.video.currentTime >= this.endSec) {
        this.$refs.video.pause();
      }
    },
    ended() {
      this.$refs.video.currentTime = this.startSec;
    }
  }
};
</script>
