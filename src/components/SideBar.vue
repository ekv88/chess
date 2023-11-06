<template>
  <div class="sidebar">
    <h3>Game history</h3>
    <ul class="history">
      <li v-for="move in gameHistory" :key="move">{{ move }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  props: {
    gameHistory: Array,
  },
}
</script>

<style scoped>
.sidebar {
  max-width: 30%;
  min-width: 300px;
  background: #4b4847;
  color: #efefef;
  margin-right: 20px;
  overflow: hidden;
  transition: min-width 0.3s ease-in-out;
}

.history {
  padding: 10px 10px 150px 10px;
  overflow-y: auto;
  max-height: 100%;
}
.history > li {
  display: block;
  border: 1px solid #b6b6b6;
  background: #777777;
  padding: 5px;
  margin: 5px 0;
  text-align: center;
}
.history > li:last-child {
  margin-bottom: 80px;
}

@media (max-width: 1023px) {
  .sidebar {
    min-width: 150px;
  }
  .sidebar > h3 {
    font-size: 16px;
  }
}

@media (max-width: 767px) {
  .sidebar {
    max-width: 100%;
    margin: 20px 0 0 0;
    height: auto;
  }
  .history {
    height: 200px;
  }
  .history > li:last-child {
    margin-bottom: 5px;
  }
}
</style>
