<template>
  <div>
    <div
      style="height: 60px; width: 100px; outline: 1px solid red; position: relative;  margin:10px"
    >
      <vue-draggable-resizable
        :x="value[0]"
        :w="10"
        :h="60"
        :parent="true"
        :axis="axis"
        :handles="['ml', 'mr']"
        :active="true"
        :prevent-deactivation="true"
        :draggable="false"
        @resizing="onResize"
      >
        <div class="child"></div>
        <p></p>
      </vue-draggable-resizable>
    </div>
    <div>
      <vue-slider
        ref="slider"
        v-model="value"
        :enable-cross="false"
      ></vue-slider>
    </div>
  </div>
</template>
<script>
import "vue-slider-component/theme/default.css";

export default {
  data: function() {
    return {
      width: 10,
      height: 0,
      axis: "x",
      x: 0,
      value: [0, 30]
    };
  },
  computed: {},
  methods: {
    onResize: function(x, _, width) {
      this.x = x;
      this.width = width;
    },
    test: function() {
      console.log(this.$refs.slider.getValue());
    }
  }
};
</script>

<style>
.child {
  outline: solid 2px blue;
  height: 100%;
}
</style>
