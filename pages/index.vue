<template>
  <div class="app">
    <div class="title-section">
      <div class="container">
        <h1 class="title">
          <span data-content="цены joki joya в санкт-петербурге">цены joki joya в санкт-петербурге</span>
        </h1>
      </div>
    </div>
    <div class="menu-section">
      <div class="container">
        <div class="tab-menu">
          <button
            v-for="(tab, idx) in tabs"
            :key="idx"
            :class="['tab-button', { active: currentTab === tab.comp }]"
            @click="currentTab = tab.comp"
          >
            <img :src="require(`@/assets/img/${tab.img}`)" /> {{ tab.title }}
          </button>
        </div>
      </div>
    </div>
    <keep-alive>
      <component v-bind:is="currentTab" class="tab"></component>
    </keep-alive>
  </div>
</template>

<script>
import Tickets from '../components/Tickets.vue'
import Rooms from '../components/Rooms.vue'
import Table from '../components/Table.vue'
import Kitchen from '../components/Kitchen.vue'
import Decorations from '../components/Decorations.vue'
export default {
  data() {
    return {
      currentTab: "Tickets",
      tabs: [
        {
          title: "Билеты",
          comp: "Tickets",
          img: "tickets.png"
        },
        {
          title: "Комнаты",
          comp: "Rooms",
          img: 'rooms.png'
        },
        {
          title: "Столы",
          comp: "Table",
          img: 'dinner-table.png'
        },
        {
          title: "Рестораны",
          comp: "Kitchen",
          img: 'kitchen.png'
        },
        {
          title: "Праздники",
          comp: "Decorations",
          img: 'decorations.png'
        },
      ]
    }
  },
  components: {
    Tickets,
    Rooms,
    Table,
    Kitchen,
    Decorations
  },
}
</script>

<style lang="scss">
.app {
  background-image: url("~assets/img/wave.png");
  background-position-x: calc(100% + 60px);
  background-position-y: 3%;
}

.container {
  max-width: 1130px;
  margin: 0 auto;
}
.title-section {
  margin-bottom: 54px;
  margin-top: 59px;
}
.title {
  font-family: 'Marvin-Round';
  
  color: #cda472;
  font-size: 52px;
  font-weight: 400;
  font-style: normal;
  letter-spacing: normal;
  line-height: 51.75px;
  text-align: center;
  position: relative;
}
.title > span {
  background: linear-gradient(-2deg, #cca06a 0%, #d3ab78 30%, #b17c3b 70%, #e4c6a8 100%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  position: relative;
  display: block;
  &:after {
    content: attr(data-content);
    color: #cca06a;
    position: absolute;
    left: 0;
    -webkit-text-stroke-width: 10px;
    -webkit-text-stroke-color: #fff;
    width: 100%;
    text-shadow: 6px 6px 5px rgb(0 0 0 / 30%);
    z-index: -1;
    top: 0;
  }
}
.tab-button {
  font-family: 'Roboto-Regular';
  background: #e1e8eb;
  color: #758185;
  font-weight: 400;
  font-size: 24px;
  letter-spacing: -0.6px;
  height: 91px;
  max-width: 223px;
  width: 100%;
  margin-right: 3px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}
.active {
  background: #758185;
  color: #ffff;
}
.tab-menu {
  display: flex;
  justify-content: center;

}
</style>
