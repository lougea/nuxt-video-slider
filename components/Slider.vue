<template>
  <div>
    <vue-slider
      v-model="value"
      :enable-cross="false"
      :min="minMax[0]"
      :max="minMax[1]"
      @change="getValueSlider($event)"
    ></vue-slider>
  </div>
</template>
<script>
import "vue-slider-component/theme/default.css";
export default {
  data: function() {
    return {
      value: [0, 30],
      minMax: [0, 100]
    };
  },
  methods: {
    getValueSlider: function(event) {
      this.value = event;
      this.$emit("sliderValue", {
        start: event[0] / 100,
        end: event[1] / 100
      });
      this.$emit("minMax", this.minMax);
    }
  }
};
</script>
