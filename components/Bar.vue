<template>
  <div>
    <div
      style="height: 60px; width: 500px; outline: 1px solid red; position: relative;  margin:10px"
    >
      <vue-draggable-resizable
        :x="x"
        :w="100"
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
      </vue-draggable-resizable>
    </div>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      width: 60,
      height: 0,
      axis: "x",
      x: 0
    };
  },
  methods: {
    onResize: function(x, _, width) {
      this.x = x;
      this.width = width;
    }
  }
};
</script>

<style>
.child {
  outline: solid 2px blue;
  height: 100%;
}
.handle {
  position: absolute;
  background-color: pink;
  border: 1px solid black;
  border-radius: 50%;
  height: 14px;
  width: 14px;

  -webkit-transition: all 300ms linear;
  -ms-transition: all 300ms linear;
  transition: all 300ms linear;
}

.handle-ml {
  top: 50%;
  margin-top: -7px;
  left: -14px;
  cursor: w-resize;
}

.handle-mr {
  top: 50%;
  margin-top: -7px;
  right: -14px;
  cursor: e-resize;
}

.handle-ml:hover,
.handle-mr:hover {
  background-color: red;
  transform: scale(1.4);
}
</style>
