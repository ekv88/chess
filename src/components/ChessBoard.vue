<template>
  <div class="flex-wrap">
    <div class="board-wrap">
      <div class="chessboard">
        <div class="corner" />
        <div v-for="file in files" :key="file" class="file-label">{{ file }}</div>
        <template v-for="rank in ranks" :key="'rank-' + rank">
          <div class="rank-label">{{ rank }}</div>
          <div
            v-for="file in files"
            :key="file + rank"
            class="square"
            :class="{
              'light-square': isLightSquare(file, rank),
              'dark-square': !isLightSquare(file, rank)
            }"
            @click="handleClick(file, rank)"
          />
        </template>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ChessBoard',
  setup() {
    const files = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];
    const ranks = [8, 7, 6, 5, 4, 3, 2, 1];

    function isLightSquare(file, rank) {
      const isEvenRank = ranks.indexOf(rank) % 2 === 0;
      return files.indexOf(file) % 2 === 0 ? isEvenRank : !isEvenRank;
    }

    return {
      files,
      ranks,
      isLightSquare,
    };
  },
  methods: {
    handleClick(file, rank) {
      this.$emit('updateHistory', `${file}${rank}`);
    },
  },
}
</script>

<style scoped>
.flex-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.board-wrap {
  min-width: 50%;
}

.chessboard {
  display: grid;
  grid-template-columns: 20px repeat(8, 1fr);
  gap: 0;
}

.corner {
  grid-column: 1;
  grid-row: 1;
}

.file-label,
.rank-label {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #dedede;
  font-weight: bold;
  font-size: 16px
}

.rank-label {
  border-right: 1px solid #333;
}

.square {
  display: flex;
  align-items: center;
  justify-content: center;
  border-top: 1px solid #333;
  border-right: 1px solid #333;
  aspect-ratio: 1;
  cursor: pointer;
}
.square:active {
  box-shadow: inset 0 0 15px #2f2f2f;
}
.square:nth-last-child(-n+8):nth-child(n) {
  border-bottom: 1px solid #333;
}

.light-square {
  background-color: #f1daaf;
}
.light-square:hover {
  background-color: #fce8d4;
}

.dark-square {
  background-color: #a67851;
}
.dark-square:hover {
  background-color: #d5a281;
}

@media (max-width: 1023px) {
  .board-wrap {
    width: 80%;
  }
}
@media (max-width: 767px) {
  .board-wrap {
    width: 100%;
  }
}
</style>
