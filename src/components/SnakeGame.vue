<script setup>
import { ref, onMounted } from 'vue'

const gameCanvasRef = ref(null)

onMounted(() => {
  const canvas = document.createElement('canvas')
  canvas.width = 400
  canvas.height = 400

  gameCanvasRef.value.appendChild(canvas)
})
</script>

<template>
  <div id="game-section">
    <div class="container">
      <div id="displays">
        <div>
          <span>Score:</span>
          <h2>00</h2>
        </div>

        <div>
          <span>Best:</span>
          <h2>00</h2>
        </div>
      </div>

      <div id="game-canvas" ref="gameCanvasRef"></div>

      <div id="author">
        <h1>SNAKE</h1>
        <span>by Burnett Miao</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
#game-section {
  color: #6e7888;
  width: 100vw;
  height: 100vh;
  background-color: #222738;
}

#author {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

#displays {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 3rem;
}

#displays div {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

#displays div span {
  padding-top: 0.4rem;
}

#displays div h2 {
  font-size: 32px;
}

#author > h1 {
  font-weight: 900;
  font-size: 26px;
}
</style>
