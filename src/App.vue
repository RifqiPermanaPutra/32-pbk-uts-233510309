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
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
</script>
