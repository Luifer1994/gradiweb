<template>
  <div class="container mt-5">
    <div class="row">
     <Slider></Slider>
      <Detail></Detail>
    </div>
  </div>
</template>

<script>
import Slider from "../components/Slider.vue";
import Detail from "../components/Detail.vue";
export default {
  name: "Home",
  components: {
    Slider,
    Detail
  },
};
</script>
