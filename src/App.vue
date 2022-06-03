<template>
  <div id="app">
    <card :data="cardsdata" />
  </div>
</template>

<script>
import card from "./components/BaseCardGrid.vue";
export default {
  name: "App",
  data() {
    return {
      cardsdata: [
        {
          title: "d1",
          number: 290,
          icon: "bx bxs-playlist",
        },
        {
          title: "d2",
          number: 2600,
          icon: "bx bxs-ev-station",
        },
        {
          title: "d3",
          number: 250,
          icon: "bx bxs-ev-station",
        },
        {
          title: "d4",
          number: 230,
          icon: "fa-solid fa-baby",
        },
      ],
    };
  },
  components: {
    card,
  },
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
</style>
