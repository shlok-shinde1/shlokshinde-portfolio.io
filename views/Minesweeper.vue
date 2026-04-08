<script setup>
const rows = 9
const cols = 9
const mineCount = 10
const mineIcon = "/assets/win95Icons/mine.svg"
const flagIcon = "/assets/win95Icons/flag.svg"

const board = ref([])
const gameOver = ref(false)
const won = ref(false)
const flagsLeft = ref(mineCount)

const makeCell = () => ({
  mine: false,
  revealed: false,
  flagged: false,
  adjacent: 0,
})

const inBounds = (r, c) => r >= 0 && r < rows && c >= 0 && c < cols

const neighbors = (r, c) => {
  const out = []
  for (let dr = -1; dr <= 1; dr++) {
    for (let dc = -1; dc <= 1; dc++) {
      if (dr === 0 && dc === 0) continue
      const nr = r + dr
      const nc = c + dc
      if (inBounds(nr, nc)) out.push([nr, nc])
    }
  }
  return out
}

const initBoard = () => {
  board.value = Array.from({ length: rows }, () =>
    Array.from({ length: cols }, () => makeCell())
  )
  gameOver.value = false
  won.value = false
  flagsLeft.value = mineCount

  let placed = 0
  while (placed < mineCount) {
    const r = Math.floor(Math.random() * rows)
    const c = Math.floor(Math.random() * cols)
    const cell = board.value[r][c]
    if (cell.mine) continue
    cell.mine = true
    placed++
  }

  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      if (board.value[r][c].mine) continue
      board.value[r][c].adjacent = neighbors(r, c).reduce((sum, [nr, nc]) => {
        return sum + (board.value[nr][nc].mine ? 1 : 0)
      }, 0)
    }
  }
}

const revealAllMines = () => {
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      const cell = board.value[r][c]
      if (cell.mine) cell.revealed = true
    }
  }
}

const floodReveal = (startR, startC) => {
  const q = [[startR, startC]]
  while (q.length) {
    const [r, c] = q.shift()
    const cell = board.value[r][c]
    if (cell.revealed || cell.flagged) continue
    cell.revealed = true
    if (cell.adjacent !== 0) continue
    for (const [nr, nc] of neighbors(r, c)) {
      const next = board.value[nr][nc]
      if (!next.revealed && !next.mine) q.push([nr, nc])
    }
  }
}

const checkWin = () => {
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      const cell = board.value[r][c]
      if (!cell.mine && !cell.revealed) return
    }
  }
  won.value = true
  gameOver.value = true
}

const revealCell = (r, c) => {
  if (gameOver.value) return
  const cell = board.value[r][c]
  if (cell.revealed || cell.flagged) return
  if (cell.mine) {
    cell.revealed = true
    gameOver.value = true
    revealAllMines()
    return
  }
  floodReveal(r, c)
  checkWin()
}

const toggleFlag = (r, c) => {
  if (gameOver.value) return
  const cell = board.value[r][c]
  if (cell.revealed) return
  if (!cell.flagged && flagsLeft.value === 0) return
  cell.flagged = !cell.flagged
  flagsLeft.value += cell.flagged ? -1 : 1
}

onMounted(initBoard)
</script>

<template>
<div class="game-wrap">
  <div class="header">
    <span>Mines: {{ mineCount }}</span>
    <span>Flags: {{ flagsLeft }}</span>
    <button class="reset" @click="initBoard">New Game</button>
  </div>

  <div class="status" v-if="won">You win!</div>
  <div class="status" v-else-if="gameOver">Boom! Try again.</div>

  <div class="board">
    <div v-for="(row, r) in board" :key="`r-${r}`" class="row">
      <button
        v-for="(cell, c) in row"
        :key="`c-${c}`"
        class="cell"
        :class="{ revealed: cell.revealed }"
        @click="revealCell(r, c)"
        @contextmenu.prevent="toggleFlag(r, c)"
      >
        <img v-if="cell.flagged && !cell.revealed" :src="flagIcon" alt="Flag" class="tile-icon" />
        <img v-else-if="cell.revealed && cell.mine" :src="mineIcon" alt="Mine" class="tile-icon" />
        <span v-else-if="cell.revealed && cell.adjacent > 0">{{ cell.adjacent }}</span>
      </button>
    </div>
  </div>
  <p class="hint">Tip: right-click to place a flag.</p>
</div>
</template>

<style scoped>
.game-wrap {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.header {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
}
.reset {
  margin-left: auto;
  padding: 2px 8px;
}
.status {
  font-size: 12px;
  font-weight: 700;
}
.board {
  display: inline-block;
  border: 2px solid #808080;
}
.row {
  display: flex;
}
.cell {
  width: 28px;
  height: 28px;
  border: 1px solid #9b9b9b;
  background: #c0c0c0;
  font-weight: 700;
  font-size: 13px;
  line-height: 1;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
.cell.revealed {
  background: #e9e9e9;
}
.tile-icon {
  width: 16px;
  height: 16px;
}
.hint {
  margin: 0;
  font-size: 11px;
  color: #4a4a4a;
}
</style>
