<template>
<div class="tickets">
  <div class="tickets__container">
    <h3 class="tickets__title">цены на вход и пользование<br> всеми аттракционами</h3>
  </div>
  <div class="tariff">
      <div class="tariff__weekdays">
        <p class="tariff__text">Будни</p>
        <div class="tariff__info">
          <div class="tariff__block">
            <img :src="require(`@/assets/img/small-infinity.png`)" />
            <div>
              <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
              <p class="tariff__price-large">950 руб.</p>
            </div>
          </div>
          <div class="tariff__block">
            <img :src="require(`@/assets/img/hour.png`)" />
            <div>
              <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
              <p class="tariff__price-large">950 руб.</p>
            </div>
          </div>
          <div class="tariff__block">
            <img :src="require(`@/assets/img/next.png`)" />
            <div>
              <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
              <p class="tariff__price-large">950 руб.</p>
            </div>
          </div>
        </div>
      </div>
      <div class="tariff__weekend">
        <p class="tariff__text">выходные <br><span class="tariff__text-dop">и праздничные дни</span></p>
        <div class="tariff__info">
          <img :src="require(`@/assets/img/infinity.png`)" />
          <p class="tariff__price">Входной билет <br><span class="tariff__price-dop">(на целый день)</span></p>
          <p class="tariff__price-large">950 руб.</p>
        </div>
      </div>
    </div>
</div>
</template>
<style scoped lang="scss">
.tickets {
  width: 100%;
  &__title{
    margin-top: 84px;
    margin-bottom: 62px;
    font-family: 'Roboto-Black';
    font-size: 30px;
    font-weight: 400px;
    color: #758185;
    text-transform: uppercase;
    letter-spacing: 6px;
  }
}
.tariff {
  background: #fafbfc;
  display: flex;
  justify-content: center;
  justify-content: space-evenly;
  &__text {
    font-family: 'Roboto-Bold';
    font-size: 36px;
    line-height: 25px;
    font-weight: 700;
    color: #758185;
    text-transform: uppercase;
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
  &__block {
    display: flex;
    align-items: center;
    &:first-child {
      margin-bottom: 34px;
    }
    &:nth-child(2) {
      margin-bottom: 34px;
    }
  }
  &__block > img {
    height: 100%;
    margin-right: 16px;
  }
}
</style>