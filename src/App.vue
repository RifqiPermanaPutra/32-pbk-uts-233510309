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
    </div>
  </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
</script>
