<template>
<div class="tickets">
  <img src="~assets/img/balloon.png" class="tickets__balloon" />
  <div class="tickets__caption">
    <div class="container">
      <h3 class="tickets__title">цены на вход и&nbsp;пользование<br> всеми аттракционами</h3>
    </div>
  </div>

  <div class="tariff">
    <div class="container">
      <div class="tariff__wrap">
        <div class="tariff__block">
          <div class="tariff__tickets">
            <div class="tariff__weekdays">
              <p class="tariff__text">Будни</p>
              <div class="tariff__info" v-if="weekdays">
                <div class="tariff__item" v-for="(weekdaysTicket, idx) in weekdays" :key="idx">
                  <img src="~/assets/img/small-infinity.png" alt="картинка" />
                  <div>
                    <p class="tariff__price">Входной билет<br><span class="tariff__price-dop">(на целый день)</span></p>
                    <p class="tariff__price-large">{{weekdaysTicket.price}} руб.</p>
                  </div>
                </div>
                <div class="tariff__item">
                  <img src="~/assets/img/hour.png" alt="картинка" />
                  <div>
                    <p class="tariff__price">Билет на 1 час</p>
                    <p class="tariff__price-large">350 руб.</p>
                  </div>
                </div>
                <div class="tariff__item">
                  <img src="~/assets/img/next.png" alt="картинка" />
                  <div>
                    <p class="tariff__price">Продление <br><span class="tariff__price-dop">(до полного дня)</span></p>
                    <p class="tariff__price-large">100 руб.</p>
                  </div>
                </div>
              </div>
            </div>
            <div class="tariff__weekend" v-if="weekend">
              <p class="tariff__text">выходные <br><span class="tariff__text-dop">и праздничные дни</span></p>
              <div class="tariff__info" v-for="(weekendTicket, idx) in weekend" :key="idx">
                <img src="~/assets/img/infinity.png" alt="картинка" />
                <p class="tariff__price">Входной билет</p>
                <span class="tariff__price-dop">(на целый день)</span>
                <p class="tariff__price-large">{{weekendTicket.price}} руб.</p>
              </div>
            </div>
          </div>
          <button class="tariff__buy">КУПИТЬ БИЛЕТ</button>
        </div>
        <div class="tariff__picture">
          <img src="~/assets/img/child.png" alt="картинка" />
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
  position: relative;
  &__title{
    font-family: 'Roboto-Black';
    font-size: 30px;
    font-weight: 400px;
    color: #758185;
    text-transform: uppercase;
    letter-spacing: 6px;
    text-align: center;
    @media (max-width: 628px) {
      font-size: 20px;
    }
  }
  &__caption {
    padding: 84px 20px 62px;
  }
  &__balloon {
    position: absolute;
    left: 10%;
    @media (max-width: 1000px) {
      display: none;
    }
  }
}
.tariff {
  background: #fafbfc;
  padding: 58px 20px 63px;
  background-image: url("~assets/img/wave2.png");
  background-position-x: 92%;
  background-position-y: 18%;
  background-repeat: no-repeat;
  overflow: hidden;
  @media (max-width: 768px) {
    background-position-y: 55%;
  }
  &__wrap {
    display: flex;
    @media (max-width: 768px) {
      flex-direction: column;
    }
  }
  &__block {
    width: 70%;
    display: flex;
    flex-direction: column;
    @media (max-width: 768px) {
      width: 100%;
    }
  }
  
  &__tickets {
    display: flex;
    justify-content: center;
    justify-content: space-evenly;
  }
  &__text {
    font-family: 'Roboto-Bold';
    font-size: 36px;
    line-height: 20px;
    font-weight: 700;
    color: #758185;
    text-transform: uppercase;
    text-align: center;
    border-bottom: 3px solid #fcc302;
    padding-top: 15px;
    height: 75px;
    @media (max-width: 628px) {
      font-size: 21px;
    }
  }
  &__weekdays {
    width: 50%;
    border-right: 3px solid #fcc302;
    padding-bottom: 30px;
  }
  &__weekend {
    width: 50%;
  }
  &__text-dop {
    font-size: 14px;
    @media (max-width: 400px) {
      font-size: 10px;
    }
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
    @media (max-width: 400px) {
      width: 75px;
    height: 30px;
    }
  }
  &__price {
    font-family: 'Roboto-Regular';
    font-weight: 400;
    font-size: 24px;
    line-height: 18px;
    @media (max-width: 628px) {
      font-size: 20px;
    }
  }
  &__price-dop {
    font-size: 16px;
  }
  &__price-large {
    font-family: 'Roboto-Bold';
    font-size: 36px;
    font-weight: 700;
    @media (max-width: 628px) {
      font-size: 20px;
    }
  }
  &__item {
    display: flex;
    align-items: center;
    &:nth-child(n + 2) {
      margin-top: 44px;
    }
    @media (max-width: 400px) {
      flex-wrap: wrap;
    }
  }
  &__item > img {
    height: 100%;
    margin-right: 16px;
    @media (max-width: 400px) {
      margin-bottom: 16px;
    }
  }
  &__picture {
    align-self: stretch;
    position: relative;
    @media (max-width: 1100px) {
      width: 30%;
    }
    @media (max-width: 768px) {
      display: none;
    }
  }
  &__picture > img {
    height: 100%;
    position: absolute;
    bottom: 0;
    @media (min-width: 1100px) and (max-width: 1300px) {
      height: 90%;
    }
    @media (max-width: 1100px) {
      height: auto;
      width: 100%;
    }
  }
  &__buy {
    font-family: 'Roboto-Bold';
    font-weight: 700;
    font-size: 26px;
    letter-spacing: 2.2px;
    line-height: 20px;
    text-align: center;
    padding: 31.5px 85px;
    color: #ffff;
    background: #fcc302;
    align-self: center;
    transition: 0.5s;
    margin: 110px 0 63px;
    @media (max-width: 628px) {
      font-size: 21px;
      padding: 21.5px 65px;
      margin: 80px 0 43px;
    }
    &:hover {
      background: #ffd240;
    }
  }
}
</style>