<template>
  <div>
    <vue-slider
      v-model="value"
      :enable-cross="false"
      :min="0"
      @change="test($event)"
    ></vue-slider>
  </div>
</template>
<script>
import "vue-slider-component/theme/default.css";
export default {
  data: function() {
    return {
      value: [0, 30]
    };
  },
  methods: {
    test: function(event) {
      this.value = event;
      this.$emit("sliderValue", {
        start: event[0] / 100,
        end: event[1] / 100
      });
    }
  }
};
</script>
