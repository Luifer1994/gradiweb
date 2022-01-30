<template>
  <div class="container mt-5 mb-5">
    <div class="row">
     <Slider :images="images"></Slider>
      <Detail :product="product"></Detail>
    </div>
  </div>
</template>

<script>
import Slider from "../components/Slider.vue";
import Detail from "../components/Detail.vue";
import axios from "axios"
export default {
  name: "Home",
  components: {
    Slider,
    Detail
  },
  data(){
    return{
      images:null,
      product:{}
    }
  },
  mounted(){
    this.getProduct()
  },
  methods:{
  async  getProduct(){
    const res = await axios.get("https://graditest-store.myshopify.com/products/free-trainer-3-mmw.js")
    this.images = res.data.media
    this.product = res.data
    console.log(res.data);
  },
  }
};
</script>
