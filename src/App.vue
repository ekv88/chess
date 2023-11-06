<template>
  <div class="app">
    <SideBar :gameHistory="gameHistory" />
    <ChessBoard @updateHistory="updateHistory"/>
  </div>
</template>

<script>
import SideBar from './components/SideBar.vue'
import ChessBoard from './components/ChessBoard.vue'

export default {
  name: 'App',
  components: {
    SideBar,
    ChessBoard,
  },
  data() {
    return {
      gameHistory: [],
    };
  },
  methods: {
    updateHistory(move) {
      this.gameHistory.push(move);
    },
  },
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333;
  width: 100%;
  height: 100%;
}
.app {
  display: flex;
  height: 100vh;
  width: 100%;
}

@media (max-width: 767px) {
  .app {
    flex-direction: column-reverse;
    height: auto;
  }
}
</style>
