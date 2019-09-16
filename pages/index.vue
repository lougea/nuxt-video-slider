<template>
  <div class="container">
    <Video />
    <Bar />
  </div>
</template>

<script>
import Bar from "~/components/Bar.vue";
import Video from "~/components/Video.vue";

export default {
  components: {
    Bar,
    Video
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
