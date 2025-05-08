<template>
  <div class="dashboard">
    <header class="header">
      <h1>Game yang telah Ditamatkan</h1>
      <div class="underline"></div>
    </header>
<!-- Input Menambahkan  Game -->
    <div class="input-group">
      <input v-model="newGame" placeholder="Tambahkan game" @keyup.enter="addGame" />
      <button @click="addGame"><span>Tambah</span> +</button>
    </div>
 <!-- Filter Mana yg belum selesai -->
    <div class="filter-buttons">
      <button :class="{ active: !showOnlyUnfinished }" @click="showOnlyUnfinished = false">Telah Tamat</button>
      <button :class="{ active: showOnlyUnfinished }" @click="showOnlyUnfinished = true">Belum Tamat</button>
    </div>
   <!-- List Game -->
    <div class="list-area">
      <template v-if="filteredGames.length">
        <ul class="game-list">
          <li
            v-for="(game, index) in filteredGames"
           :key="index"
           :class="{ finished: game.finished }"
            >
              <button class="status-btn" @click="toggleFinished(index)">
                {{ game.finished ? '✅ ' : '⏳' }}
             </button>
            <span>{{ game.name }}</span>
            <button @click="removeGame(index)">🗑️</button>
          </li>

        </ul>
      </template>

      <div v-else class="empty-state">
        <p>Belum ada Game yang ingin ditampilkan</p>
      </div>
    </div>

    <!--Bagian Status 3 dibawah-->
    <div class="stats-container">
  <div class="stat-box stat-total">
    <div class="stat-title">Total Game</div>
    <div class="stat-value">{{ games.length }}</div>
  </div>
  <div class="stat-box stat-done">
    <div class="stat-title">Tamat</div>
    <div class="stat-value">{{ games.filter(g => g.finished).length }}</div>
  </div>
  <div class="stat-box stat-pending">
    <div class="stat-title">Belum Tamat</div>
    <div class="stat-value">{{ games.filter(g => !g.finished).length }}</div>
  </div>
</div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const newGame = ref('')
const showOnlyUnfinished = ref(false)

const games = ref([
  { name: 'Resident Evil 4 Remake', finished: true },
  { name: 'Baldur’s Gate 3', finished: false },
  { name: 'Marvel Spiderman 2', finished: true },
])

</script>
