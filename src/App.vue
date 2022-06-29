<template>
  <div id="app">
   <card :data='cardsdata'/>
  </div>
</template>

<script>

import card from './components/card.vue'
export default {
  name: 'App',
   data () {
    return {
        cardsdata:[
            {
                title:'card1',
                number:290,
                icon:'bx bxs-playlist',
            },
            {
                title:'card2',
                number:2600,
                icon:'bx bxs-ev-station',
            },
           {
                title:'d3',
                number:3500,
                icon:'fa fa-edit',
            },
           {
                title:'d4',
                number:2000,
                icon:'fa-solid fa-trash',
            }
        ]
    }
  },
  components: {
    card
  }
}
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
