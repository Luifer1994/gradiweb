<template>
    <!-- Modal -->
  <div
    class="modal fade"
    id="infoCart"
    data-bs-backdrop="static"
    data-bs-keyboard="false"
    tabindex="-1"
    aria-labelledby="staticBackdropLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="staticBackdropLabel">Information of your cart</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
            <div class="row">
                <div class="col-md-5 col-sm-12">
                    <img :src="data.img" class="img-fluid" alt="...">
                </div>
                <div class="col-md-7 col-sm-12 text-start">
                    <h4>{{ data.title }}</h4>
                    <h5>Color: <span class="badge rounded-pill" :style="{ 'background-color': data.color  }">{{ data.color }}</span></h5>
                    <h5>Size: {{ data.size }}</h5>
                     <h5>Mounted: {{ data.amount }}</h5>
                      <h3>Total: $ {{ data.total }}</h3>
                </div>
            </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-danger" data-bs-dismiss="modal">
            Close
          </button>
          <button type="button" class="btn btn-dark">Checkout</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
    name:"ModalCart",
    props:{
        data:Object
    }
}
</script>