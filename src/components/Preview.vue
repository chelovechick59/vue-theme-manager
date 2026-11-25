
<script setup lang="ts">
import { computed } from 'vue'
import type { Theme } from '../types'

const props = defineProps<{
  theme: Theme
}>()

const themeStyles = computed(() => ({
  '--background-color': props.theme.backgroundColor,
  '--card-color': props.theme.cardColor,
  '--text-color': props.theme.textColor,
  '--button-color': props.theme.buttonColor,
  '--border-color': props.theme.borderColor,
  '--font-size': props.theme.fontSize + 'px',
  '--border-radius': props.theme.borderRadius + 'px',
  '--border-width': props.theme.borderWidth + 'px',
  '--border-style': props.theme.borderStyle
}))
</script>

<template>
  <section class="preview" :style="themeStyles">
    <h2>Попередній перегляд</h2>

    <article class="card">
      <h3>Приклад картки</h3>

      <p>
        Змінюйте кольори, розмір шрифту,
        заокруглення та стиль рамки
        в реальному часі.
      </p>

      <button>Детальніше</button>
    </article>
  </section>
</template>

<style scoped>
.preview {
  padding: 25px;
  background-color: var(--background-color);
  color: var(--text-color);
  font-size: var(--font-size);
  border-radius: var(--border-radius);
  transition: background-color 0.15s;
}

h2 {
  margin-top: 0;
  font-size: 1.5em;
}

h3 {
  margin-top: 0;
  font-size: 1.2em;
}

p {
  line-height: 1.6;
}

.card {
  padding: 22px;

  background-color: var(--card-color);
  border-color: var(--border-color);
  border-width: var(--border-width);
  border-style: var(--border-style);
  border-radius: var(--border-radius);
}

button {
  padding: 10px 20px;
  border: none;

  background-color: var(--button-color);
  color: white;
  font-size: inherit;
  border-radius: var(--border-radius);

  cursor: pointer;
}

button:hover {
  filter: brightness(0.9);
}
</style>
