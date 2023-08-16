<template>
  <div class="modal-rate"
      v-if="isActiveModal"
    >
    <div class="modal-content">
      <div class="sale-package">
        <div class="sale-item">-10%</div>
        <div class="sale-text">скидка на все пакеты</div>
      </div>
      <div class="modal-header">
        <div class="header-text">Выберите подходящий тариф</div>
        <div class="header-tabs">
          <div class="header-tabs-item"
            v-for="(tabItem, idx) in tabsItemList"
            :class="{'active': tabsItemList[idx] == currentTab }"
            :key="idx"
            @click="clickTabs(idx)"
          >{{tabItem.title}}</div>
        </div>
      </div>
      <div class="tariff-package-wrapper">
        <div class="tariff-package">
          <div class="package-item">
          <div class="package-title">Одиночный пакет</div>
          <div class="package-price">890 &#x20bd<span> / <del>1430 &#x20bd</del></span></div>
          </div>
          <div class="package-item">
          <div class="package-conditions-list">
            <div class="conditions-item"
              v-for="(conditions,idx) in currentTab.conditioanaList"
              :key="idx"
            >
              <div class="conditions-title" :class="conditions.class"><div class="conditions-checkbox"><img :src="require(`../assets/${conditions.src}.svg`)" alt=""></div> {{ conditions.title }}</div>
            </div>

          </div>
          </div>
          <div class="package-item">
          <div class="subscribe-button">Оформить подписку</div>
          <div class="trial-button">Триал на 2 дня</div>
          </div>
        </div>
        <div class="footer-tariff-package">
          <div class="footer-tariff-package-text">Даем 1 000 000 виртуальной валюты на эмулятор</div>
        </div>
      </div>
    </div>
      <div class="close"
            @click="isActiveModal = false"
      ></div>
  </div>
</template>

<script setup>
defineProps({
  isActiveModal:Boolean
})
</script>
<script>
export default {
  data() {
    return {
      tabsItemList:[
        {title: "На месяц",},
        {
          title: "На пол года",
          conditioanaList: [
            { title: 'Доступ к эмулятору', src: 'checkCircle', class:'active'},
            { title: 'Доступ к боевому режиму', src: 'checkCircle', class:'active' },
            { title: 'Создание проп группы на 10 чел.', src: 'unCheckCircle'},
            {title:'Обучающие группы на 10 чел.', src:'unCheckCircle'},
          ]
        },
        {
          title: "На год",
           conditioanaList: [
            { title: 'Доступ к эмулятору', src: 'checkCircle', class:'active'},
            { title: 'Доступ к боевому режиму', src: 'checkCircle', class:'active' },
            { title: 'Создание проп группы на 10 чел.', src: 'unCheckCircle'},
            { title: 'Обучающие группы на 10 чел.', src: 'unCheckCircle' },
            
          ]
        }
      ],
      currentTab:{title: "На месяц",}
    }
  },
  methods: {
    clickTabs(idx) {
      this.currentTab = this.tabsItemList[idx]
    }
  },
}
</script>
<style lang="scss">
@import "../assets/styles/utils.scss";

.modal-rate{
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  max-width: 989px;
  max-height: 542px;
  width: 100%;
  background-color: $whiteBlack;
  border-radius: 10px;
}
.modal-content{
  margin: 80px;
}
.sale-package{
  max-width: 81px;
  height: 100px;
  position: absolute;
  top: 0px;
  left: 80px;
  padding: 26px 6px;
  background: $blue;
}
.sale-package::after,.sale-package::before{
  content: '';
  position: absolute;
  bottom: -30px;
  border-top: 30px solid $blue;
}
.sale-package::after{
  right: 0;
  border-left: 50px solid transparent;

}
.sale-package::before{
  left: 0;
  border-right: 50px solid transparent;
}
.sale-item{
  background: $mono-white;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Gilroy;
  font-size: 20px;
  font-style: normal;
  font-weight: 700;
  line-height: 130%; /* 26px */
  letter-spacing: 0.1px;
  padding: 10px 4px;
  border-radius: 5px;
}
.sale-text{
  color: $mono-white;
  padding: 6px 10px;
  text-align: center;
  /* Title 1/Title 2/Medium */
  font-family: Gilroy;
  font-size: 15px;
  font-style: normal;
  font-weight: 500;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
}
.header-tabs-item,.subscribe-button,.trial-button,.close{
  cursor: pointer;
}
.modal-header{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  gap: 35px;
}
.header-text,.package-title,.package-price,.footer-tariff-package-text{
  color: $mono-white;
  text-align: center;
  font-family: Gilroy;
  font-size: 24px;
  font-style: normal;
  font-weight: 700;
  line-height: 32px; /* 133.333% */
  letter-spacing: 0.12px;
}

.header-tabs{
  display: flex;
  justify-content: space-between;
  gap: 20px;
  align-items: center;
}
.header-tabs-item{
  color: $mono-white;
  font-family: Gilroy;
  font-size: 15px;
  font-style: normal;
  font-weight: 500;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
  padding: 10px 20px;
  display: flex;
  width: 124px;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  background: $grey2;
  &.active{
    background: $purpleGradien;
  }
}
.tariff-package-wrapper{
  margin-top: 40px;
  border-radius: 10px;
  border: 1px solid $grey2;
  overflow: hidden;
  z-index:1;
}
.tariff-package{
  display: flex;
  justify-content: space-between;
  gap: 10px;
  padding: 35px 40px;
}
.footer-tariff-package-text{
  font-size: 15px;
  font-weight: 500;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
}
.footer-tariff-package{
  background: $blue;
  
  z-index: 2;
  padding: 10px 40px;
}
.package-item{
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.package-title{
  font-size: 18px;
}
.package-price{
  font-size: 18px;
  color: $yellow;
  span{
    color: $grey1;
  }
}
.conditions-title{
  display: flex;
  align-items: center; 
  gap: 8px;
  font-family: Gilroy;
  font-size: 15px;
  font-style: normal;
  font-weight: 600;
  line-height: 130%; /* 19.5px */
  letter-spacing: 0.075px;
  color: $grey1;
  &.active{
    color: $mono-white;
  }
}
.conditions-checkbox{
  width: 24px;
  height: 24px;
}
.package-conditions-list{
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.subscribe-button,.trial-button{
  max-width: 205px;
  width: calc(100% - 40px);
  height: 30px; 
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 20px;
  gap: 10px;
  flex-shrink: 0;
  color: $mono-white;
  border-radius: 5px;
  font-family: Gilroy;
  font-size: 14px;
  font-style: normal;
  font-weight: 600;
  line-height: 130%; /* 18.2px */
  letter-spacing: 0.5px
}
.subscribe-button{
  background: $grey2;
}
.trial-button{
  background: $green1;
}
.close {
  position: absolute;
  right: 32px;
  top: 32px;
  width: 32px;
  height: 32px;
}
.close:before, .close:after {
  position: absolute;
  left: 15px;
  content: ' ';
  height: 24px;
  width: 2px;
  background: $grey1;
}
.close:before {
  transform: rotate(45deg);
}
.close:after {
  transform: rotate(-45deg);
}
</style>
