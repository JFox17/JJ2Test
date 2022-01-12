<template>
<div class="tickets">
  <div class="tickets__caption">
    <div class="container">
      <h3 class="tickets__title">цены на вход и пользование<br> всеми аттракционами</h3>
    </div>
  </div>

  <div class="tariff">
    <div class="container">
      <div class="tariff__wrap">
        <div class="tariff__block">
          <div class="tariff__weekdays">
            <p class="tariff__text">Будни</p>
            <div class="tariff__info" v-if="weekdays">
              <div class="tariff__item">
                <img :src="require(`@/assets/img/small-infinity.png`)" />
                <div>
                  <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
                  <p class="tariff__price-large">950 руб.</p>
                </div>
              </div>
              <div class="tariff__item">
                <img :src="require(`@/assets/img/hour.png`)" />
                <div>
                  <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
                  <p class="tariff__price-large">950 руб.</p>
                </div>
              </div>
              <div class="tariff__item" v-for="(weekdaysTicket, idx) in weekdays" :key="idx">
                <img :src="require(`@/assets/img/next.png`)" />
                <div>
                  <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
                  <p class="tariff__price-large">{{weekdaysTicket.price}} руб.</p>
                </div>
              </div>
            </div>
          </div>
          <div class="tariff__weekend" v-if="weekend">
            <p class="tariff__text">выходные <br><span class="tariff__text-dop">и праздничные дни</span></p>
            <div class="tariff__info" v-for="(weekendTicket, idx) in weekend" :key="idx">
              <img :src="require(`@/assets/img/infinity.png`)" />
              <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
              <p class="tariff__price-large">{{weekendTicket.price}} руб.</p>
            </div>
          </div>
        </div>
        <div class="tariff__picture">
          <img :src="require(`@/assets/img/child.png`)" />
        </div>
        
      </div>
    </div>
  </div>
</div>
</template>
<script>
export default {
  data() {
    return {
      weekend: [],
      weekdays: []
    }
  },
  async fetch() {
    let prices = await this.$axios.$get('https://joki-joya.ru/api/site/city/2/prices/')
    let tickets = prices[0]
    this.weekend = tickets.filter(item => item.holidays === true)
    this.weekdays = tickets.filter(item => item.holidays === false)
    console.log(this.weekend)
  },
}
</script>

<style scoped lang="scss">
.tickets {
  width: 100%;
  &__title{
    
    font-family: 'Roboto-Black';
    font-size: 30px;
    font-weight: 400px;
    color: #758185;
    text-transform: uppercase;
    letter-spacing: 6px;
    text-align: center;
  }
  &__caption {
    margin-top: 84px;
    margin-bottom: 62px;
  }
}
.tariff {
  background: #fafbfc;
  &__wrap {
    display: flex;
  }
  
  &__block {
    display: flex;
    justify-content: center;
    justify-content: space-evenly;
    width: 70%;
  }
  &__text {
    font-family: 'Roboto-Bold';
    font-size: 36px;
    line-height: 25px;
    font-weight: 700;
    color: #758185;
    text-transform: uppercase;
    text-align: center;
    border-bottom: 3px solid #fcc302;
    height: 58px;
  }
  &__weekdays {
    width: 50%;
    border-right: 3px solid #fcc302;
  }
  &__weekend {
    width: 50%;
  }
  &__text-dop {
    font-size: 16px;
    line-height: 20px;
  }
  &__info {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #758185;
    margin-top: 38px;
  }
  &__info > img {
    width: 105px;
    height: 50px;
    margin-bottom: 32px;
  }
  &__price {
    font-family: 'Roboto-Regular';
    font-weight: 400;
    font-size: 24px;
    line-height: 18px;
  }
  &__price-dop {
    font-size: 16px;
  }
  &__price-large {
    font-family: 'Roboto-Bold';
    font-size: 36px;
    font-weight: 700;
  }
  &__item {
    display: flex;
    align-items: center;
    &:first-child {
      margin-bottom: 34px;
    }
    &:nth-child(2) {
      margin-bottom: 34px;
    }
  }
  &__item > img {
    height: 100%;
    margin-right: 16px;
  }
  &__picture {
    align-self: stretch;
    position: relative;
  }
  &__picture > img {
    height: 100%;
    position: absolute;
  }
}
</style>