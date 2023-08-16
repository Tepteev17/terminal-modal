<template>
  <div class="modal-purchase" v-if="isActiveModal">
    <div class="modal-content">
      <div class="modal-header">
        <div class="header-text">Покупка {{ coinItem.name }}</div>
        <div class="header-subhead">
          Выберите кол-во монет, которое нужно вам.
        </div>
        <div class="header-tabs">
          <div
            class="header-tabs-item"
            v-for="(quantity, idx) in coinQuantityList"
            :key="idx"
            @click="coinItem.quantity = quantity.quantity"
          >
            {{ quantity.quantity }}
          </div>
        </div>
        <div class="purchase-block-wrapper">
          <div class="block-purchase">
            <div class="left-blockpurchase-purchase">
              <div class="coin-icon">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                  fill="none"
                >
                  <circle cx="12" cy="12" r="12" fill="white" />
                  <path
                    fill-rule="evenodd"
                    clip-rule="evenodd"
                    d="M12 24C5.37225 24 0 18.6278 0 12C0 5.37225 5.37225 0 12 0C18.6278 0 24 5.37225 24 12C24 18.6278 18.6278 24 12 24ZM16.875 14.3655C16.875 12.4732 15.693 11.4045 12.9277 10.7385V7.4085C13.7827 7.584 14.601 7.95225 15.4012 8.5305L16.4205 6.8835C15.4165 6.14815 14.2373 5.68888 13.0005 5.5515V4.5H11.418V5.51625C9.144 5.69175 7.59825 6.9885 7.59825 8.88075C7.59825 10.8608 8.835 11.8245 11.4908 12.4905V15.9255C10.308 15.75 9.32625 15.2243 8.289 14.418L7.125 16.0125C8.37096 16.9717 9.85551 17.5718 11.418 17.748V19.5H13.0005V17.7653C15.3105 17.5725 16.875 16.293 16.875 14.3655ZM11.49 10.3702C10.0897 9.9675 9.74475 9.49425 9.74475 8.75775C9.74475 7.9875 10.3448 7.374 11.4908 7.28625L11.49 10.3702ZM14.7285 14.4877C14.7285 15.3292 14.0737 15.9075 12.9277 15.9952V12.8235C14.3467 13.227 14.7285 13.6995 14.7285 14.4885V14.4877Z"
                    fill="#1E68F6"
                  />
                </svg>
              </div>
              <div class="coin-quantity">{{ coinItem.quantity }}</div>
              <div class="coin-title">{{ coinItem.name }}</div>
            </div>
            <div class="right-blockpurchase-purchase">
              <div class="coin-quantity TO_CARENCY">
                <span>= </span>
                <span> {{ 86*coinItem.quantity }}</span>
                <span> &#x20bd</span>
              </div>
            </div>
          </div>
          <div class="change-quantity-block">
            <div class="icrease" @click="coinItem++"></div>
            <div class="decrease" @click="coinItem--"></div>
          </div>
        </div>
      </div>
    </div>
    <div class="close-modal">
      <div class="close" @click="isActiveModal = false"></div>
    </div>
  </div>
</template>
<script setup>
defineProps({
  isActiveModal: Boolean,
  coinItem: Object,
});
</script>
<script>
export default {
  data() {
    return {
      coinQuantityList: [
        { quantity: 1000 },
        { quantity: 5000 },
        { quantity: 10000 },
      ],
    };
  },
};
</script>
<style scoped lang="scss">
@import "../assets/styles/utils.scss";
.modal-purchase {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  max-width: 560px;
  height: 539px;
  width: 100%;
  background-color: $whiteBlack;
  border-radius: 10px;
}
.header-tabs-item {
  max-width: 100px;
  min-width: 74px;
  width: auto;
}
.modal-header {
  align-items: start;
  gap: 20px;
}
.header-tabs {
  margin-top: 20px;
  width: 100%;
  justify-content: start;
}
.header-text {
  text-align: start;
}
.header-subhead {
  color: $grey1;
  font-family: Gilroy;
  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: 24px;
  letter-spacing: 0.08px;
}
.purchase-block-wrapper{
  width: 100%;
}
.block-purchase{
  border-radius: 10px;
  background: $lightBlack;
  padding: 15px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.left-blockpurchase-purchase{
  display: flex;
  align-items: center;
  gap: 10px;
}
.coin-quantity{
   color: $mono-white;
  /* Title 1/Title 2/Semibold */
  font-family: Gilroy;
  font-size: 15px;
  font-style: normal;
  font-weight: 600;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
}
.coin-title{
  color: $grey1;
  font-family: Gilroy;
  font-size: 15px;
  font-style: normal;
  font-weight: 500;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
}
</style>
