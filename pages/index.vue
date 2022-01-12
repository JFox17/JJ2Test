<template>
  <div>
    <div class="title-section">
      <div class="container">
        <h2 class="title">
          цены joki joya в санкт-петербурге
        </h2>
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

.container {
  max-width: 1130px;
  margin: 0 auto;
}
.title-section {
  margin-bottom: 54px;
}
.title {
  font-family: 'Marvin-Round';
  background: linear-gradient(-2deg, #cca06a 0%, #d3ab78 30%, #b17c3b 70%, #e4c6a8 100%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #cda472;
  font-size: 52px;
  font-weight: 400;
  font-style: normal;
  letter-spacing: normal;
  line-height: 51.75px;
  text-align: center;
}
.tab-button {
  font-family: 'Roboto-Regular';
  background: #e1e8eb;
  color: #758185;
  font-weight: 400;
  // line-height: 108.01px;
  font-size: 24px;
  letter-spacing: -0.6px;
  // padding: 16px 25px;
  height: 91px;
  max-width: 223px;
  width: 100%;
  margin-right: 3px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  // height: 100%;
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
