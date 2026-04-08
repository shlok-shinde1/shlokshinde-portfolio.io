<script setup>
const gridSize = 16
const tickMs = 120

const snake = ref([
  { x: 7, y: 8 },
  { x: 6, y: 8 },
  { x: 5, y: 8 },
])
const direction = ref({ x: 1, y: 0 })
const pendingDirection = ref({ x: 1, y: 0 })
const food = ref({ x: 11, y: 8 })
const score = ref(0)
const gameOver = ref(false)
let timerId = null

const randomCell = () => ({
  x: Math.floor(Math.random() * gridSize),
  y: Math.floor(Math.random() * gridSize),
})

const isSnakeCell = (x, y) => snake.value.some((p) => p.x === x && p.y === y)

const placeFood = () => {
  let next = randomCell()
  while (isSnakeCell(next.x, next.y)) {
    next = randomCell()
  }
  food.value = next
}

const resetGame = () => {
  snake.value = [
    { x: 7, y: 8 },
    { x: 6, y: 8 },
    { x: 5, y: 8 },
  ]
  direction.value = { x: 1, y: 0 }
  pendingDirection.value = { x: 1, y: 0 }
  score.value = 0
  gameOver.value = false
  placeFood()
}

const setDirection = (x, y) => {
  if (direction.value.x === -x && direction.value.y === -y) return
  pendingDirection.value = { x, y }
}

const onKey = (e) => {
  if (e.key === "ArrowUp") setDirection(0, -1)
  else if (e.key === "ArrowDown") setDirection(0, 1)
  else if (e.key === "ArrowLeft") setDirection(-1, 0)
  else if (e.key === "ArrowRight") setDirection(1, 0)
}

const step = () => {
  if (gameOver.value) return

  direction.value = pendingDirection.value
  const head = snake.value[0]
  const next = {
    x: head.x + direction.value.x,
    y: head.y + direction.value.y,
  }

  if (next.x < 0 || next.x >= gridSize || next.y < 0 || next.y >= gridSize) {
    gameOver.value = true
    return
  }

  if (isSnakeCell(next.x, next.y)) {
    gameOver.value = true
    return
  }

  snake.value.unshift(next)
  if (next.x === food.value.x && next.y === food.value.y) {
    score.value += 1
    placeFood()
  } else {
    snake.value.pop()
  }
}

const boardStyle = computed(() => ({
  gridTemplateColumns: `repeat(${gridSize}, 1fr)`,
}))

const cellClass = (x, y) => {
  if (food.value.x === x && food.value.y === y) return "cell food"
  if (snake.value[0].x === x && snake.value[0].y === y) return "cell head"
  if (isSnakeCell(x, y)) return "cell body"
  return "cell"
}

onMounted(() => {
  window.addEventListener("keydown", onKey)
  timerId = setInterval(step, tickMs)
})

onBeforeUnmount(() => {
  window.removeEventListener("keydown", onKey)
  if (timerId) clearInterval(timerId)
})
</script>

<template>
<div class="snake-wrap">
  <div class="header">
    <span>Score: {{ score }}</span>
    <button class="reset" @click="resetGame">Restart</button>
  </div>
  <div v-if="gameOver" class="status">Game over - press Restart</div>
  <div class="board" :style="boardStyle">
    <div
      v-for="i in gridSize * gridSize"
      :key="i"
      :class="cellClass((i - 1) % gridSize, Math.floor((i - 1) / gridSize))"
    />
  </div>
  <p class="hint">Use arrow keys to move.</p>
</div>
</template>

<style scoped>
.snake-wrap { display: flex; flex-direction: column; gap: 8px; }
.header { display: flex; justify-content: space-between; align-items: center; font-size: 12px; }
.status { font-size: 12px; font-weight: 700; }
.board {
  width: 320px;
  height: 320px;
  display: grid;
  border: 2px solid #808080;
  background: #d9d9d9;
}
.cell { border: 1px solid rgba(0,0,0,0.05); background: #efefef; }
.cell.body { background: #2f9e44; }
.cell.head { background: #1b5e20; }
.cell.food { background: #d90429; border-radius: 2px; }
.hint { margin: 0; font-size: 11px; color: #4a4a4a; }
</style>
