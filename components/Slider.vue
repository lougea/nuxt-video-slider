<template>
  <div>
    <vue-slider
      ref="slider"
      v-model="value"
      :enable-cross="false"
      @change="test()"
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
  computed: {},
  mounted() {},
  methods: {
    test: function() {
      this.$emit("sliderValue", this.$refs.slider.getValue());
    }
  }
};
</script>
