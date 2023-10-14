<template>
  <div class="menu">
    <a v-for="(menu, key) in menus" :key="key">{{ menu }}</a>
  </div>
  <div class="bg-black" v-if="isModalOpen === true">
    상세페이지임
    <div class="bg-white">상세페이지 내용임</div>
    <button @click="click_modal">닫기</button>
  </div>
  <div v-for="(value, key) in datas" :key="key">
    <h4 @click="click_modal">{{ datas[key].title }}</h4>
    <p>{{ datas[key].price }} 원</p>
    <p>{{ datas[key].content }}</p>
    <img :src="value.image" />
    <button v-on:click="report(key)">
      <span>신고된 수: {{ report_nums[key] }}</span>
    </button>
  </div>
</template>

<script>
import datas from "./datas.js";

export default {
  name: "App",
  data() {
    return {
      datas,
      menus: ["Home", "Shop", "About"],
      report_nums: [0, 0, 0, 0, 0, 0, 0],
      my_style: "color: red",
      locates: ["천호동", "마포구", "신사동"],
      prices: [7000, 8000, 5000],
      menu: {},
      isModalOpen: false,
    };
  },
  methods: {
    report(idx) {
      this.report_nums[idx] += 1;
    },
    click_modal() {
      this.isModalOpen = !this.isModalOpen;
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
div {
  box-sizing: border-box;
}
body {
  margin: 0;
}

.menu {
  background-color: blanchedalmond;
  padding: 15px;
  border-radius: 15px;
}
.menu a {
  padding: 15px;
}
.bg-black {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.bg-white {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
