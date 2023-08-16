<template>
  <div class="modal-wrapper">
    <modalRate
      :isActiveModal="false"
    />
    <modalPurchase
      :isActiveModal="true"
      :coinItem="coinItem"
    />
  </div>
</template>

<script>
import modalRate from '@/components/modalRate.vue'
import modalPurchase from '@/components/modalPurchase.vue'
export default {
  name: 'App',
  data() {
    return {
      coinItem: {
        name: 'USDT',
        srcIcon: '',
        quantity: 0,
        minQuantity: 100
      }
    }
  },
  components: {
    modalRate,
    modalPurchase
  }
}
</script>

<style lang="scss">
@import "../src/assets/styles/utils.scss";
.modal-wrapper{
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
}

</style>
