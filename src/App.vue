
<script setup lang="ts">
import { ref } from 'vue'
import ThemeManager from './components/ThemeManager.vue'
import Preview from './components/Preview.vue'
import type { Theme } from './types'

const defaultTheme: Theme = {
  backgroundColor: '#e9edf3',
  cardColor: '#ffffff',
  textColor: '#243047',
  buttonColor: '#4263eb',
  borderColor: '#a5afbf',
  fontSize: 16,
  borderRadius: 12,
  borderWidth: 1,
  borderStyle: 'solid'
}

const theme = ref<Theme>({ ...defaultTheme })

function resetTheme() {
  theme.value = { ...defaultTheme }
}
</script>

<template>
  <div class="app">
    <header>
      <h1>Конструктор теми</h1>
      <p>Налаштування зовнішнього вигляду застосунку</p>
    </header>

    <main class="container">
      <ThemeManager
        v-model="theme"
        @reset="resetTheme"
      />

      <Preview :theme="theme" />
    </main>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f3f4f6;
  color: #243047;
}

#app {
  width: 100%;
  min-height: 100vh;
}

.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 30px;
}

header {
  text-align: center;
  margin-bottom: 30px;
}

header h1 {
  margin-bottom: 10px;
}

header p {
  color: #6b7280;
}

.container {
  display: grid;
  grid-template-columns: 320px 1fr;
  align-items: start;
  gap: 25px;
}

button,
input,
select {
  font-family: inherit;
}

@media (max-width: 750px) {
  .container {
    grid-template-columns: 1fr;
  }

  .app {
    padding: 15px;
  }
}
</style>
