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
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
</script>
