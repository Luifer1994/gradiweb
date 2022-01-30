<template>
  <div class="col-sm-6">
    <h6 class="text-secondary text-wrap text-start">by Nike x ALYX</h6>
    <h3 class="text-start">{{ product.title }}</h3>
    <h3 class="text-start text-wrap">
      $ {{ product.price }}
      <span class="text-secondary text-sm text-wrap"
        >/ $ {{ product.compare_at_price }}</span
      >
    </h3>
    <hr />
    <div v-for="option in product.options" :key="option">
      <div class="row" v-if="option.name === 'Color'">
        <div class="col col-sm-2 text-start">
          <h6 class="text-secondary text-wrap">{{ option.name }}:</h6>
        </div>
        <div class="col col-sm-4 text-start">
          <span v-for="color in option.values" :key="color">
            <input
              type="radio"
              class="btn-check"
              :id="color"
              :value="color"
              v-model="colorSelected"
            />
            <label
              class="btn btn-danger rounded-pill p-3 m-1"
              :style="{ 'background-color': color }"
              :for="color"
            ></label>
          </span>
        </div>
      </div>

      <div class="row" v-if="option.name === 'Size' && colorSelected">
        <div class="col-2 text-start">
          <h6 class="text-secondary text-wrap">{{ option.name }} :</h6>
        </div>
        <div class="col text-start">
          <div class="row">
            <div class="col" v-for="size in option.values" :key="size">
              <input
                type="radio"
                class="btn-check"
                :id="size"
                :value="size"
                v-model="sizeSelected"
              />
              <label class="btn btn-outline-secondary btn-sm m-1" style="width:50px" :for="size">{{ size }}</label>
            </div>
          </div>
        </div>
      </div>
    </div>

    <hr />
    <div class="row">
      <div class="col-6 text-start">
        <div class="btn-group" role="group" aria-label="Basic example">
          <button type="button" class="btn btn-outline-secondary" :class="{ disabled: amount === 1 }" @click="decred">-</button>
          <input class="form-control form-control-sm mx-1" style="width:60px" type="number" min="1" v-model="amount" />
          <button type="button" class="btn btn-outline-secondary" @click="add()">+</button>
        </div>
      </div>
      <div class="col text-start">
        <h4>
          Total: <span>$ {{ totalAmount() }}</span>
        </h4>
      </div>
    </div>

    <hr />
    <div class="row">
      <div class="row">
        <div class="col-sm-6 d-grid gap-2 mt-2">
          <button type="button" class="btn btn-light btn-lg px-5">Add to favorite</button>
        </div>
        <div class="col-sm-6 d-grid gap-2 mt-2">
          <button type="button" class="btn btn-dark btn-lg px-5" :class="{ disabled: !colorSelected,disabled: !sizeSelected}">
            Add to cart
          </button>
        </div>
      </div>

      <div class="col-12 text-start mt-4">
        <div v-html="product.description"></div>
      </div>
    </div>
  </div>
  
</template>
<script>
export default {
  name: "Detail",
  props: {
    product: Object,
  },
  data() {
    return {
      colorSelected: "",
      sizeSelected: "",
      total: 0,
      amount: 1,
    };
  },

  methods:{
      totalAmount(){
          return this.total = this.product.price * this.amount
      },
      add(){
          this.amount ++
      },
      decred(){
          this.amount --
      }
  }
};
</script>
