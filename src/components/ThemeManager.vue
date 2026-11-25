
<script setup lang="ts">
import type { Theme } from '../types'

const props = defineProps<{
  modelValue: Theme
}>()

const emit = defineEmits<{
  'update:modelValue': [value: Theme]
  reset: []
}>()

function updateTheme(
  key: keyof Theme,
  value: string | number
) {
  emit('update:modelValue', {
    ...props.modelValue,
    [key]: value
  })
}

function getValue(event: Event): string {
  return (event.target as HTMLInputElement).value
}

function getNumber(event: Event): number {
  return Number(getValue(event))
}
</script>

<template>
  <section class="manager">
    <h2>Налаштування теми</h2>

    <h3>Кольори</h3>

    <label class="field">
      Колір фону
      <input
        type="color"
        :value="modelValue.backgroundColor"
        @input="updateTheme('backgroundColor', getValue($event))"
      />
    </label>

    <label class="field">
      Колір карток
      <input
        type="color"
        :value="modelValue.cardColor"
        @input="updateTheme('cardColor', getValue($event))"
      />
    </label>

    <label class="field">
      Колір тексту
      <input
        type="color"
        :value="modelValue.textColor"
        @input="updateTheme('textColor', getValue($event))"
      />
    </label>

    <label class="field">
      Колір кнопок
      <input
        type="color"
        :value="modelValue.buttonColor"
        @input="updateTheme('buttonColor', getValue($event))"
      />
    </label>

    <label class="field">
      Колір рамки
      <input
        type="color"
        :value="modelValue.borderColor"
        @input="updateTheme('borderColor', getValue($event))"
      />
    </label>

    <h3>Розміри</h3>

    <label class="range-field">
      Розмір шрифту: {{ modelValue.fontSize }} px

      <input
        type="range"
        min="12"
        max="28"
        :value="modelValue.fontSize"
        @input="updateTheme('fontSize', getNumber($event))"
      />
    </label>

    <label class="range-field">
      Заокруглення: {{ modelValue.borderRadius }} px

      <input
        type="range"
        min="0"
        max="30"
        :value="modelValue.borderRadius"
        @input="updateTheme('borderRadius', getNumber($event))"
      />
    </label>

    <label class="range-field">
      Товщина рамки: {{ modelValue.borderWidth }} px

      <input
        type="range"
        min="0"
        max="6"
        :value="modelValue.borderWidth"
        @input="updateTheme('borderWidth', getNumber($event))"
      />
    </label>

    <h3>Стиль рамки</h3>

    <select
      :value="modelValue.borderStyle"
      @change="updateTheme('borderStyle', getValue($event))"
    >
      <option value="solid">Суцільна</option>
      <option value="dashed">Штрихова</option>
      <option value="dotted">Пунктирна</option>
      <option value="double">Подвійна</option>
      <option value="none">Без рамки</option>
    </select>

    <button class="reset" @click="emit('reset')">
      Скинути налаштування
    </button>
  </section>
</template>

<style scoped>
.manager {
  background: white;
  padding: 22px;
  border: 1px solid #e0e0e0;
  border-radius: 14px;
  box-shadow: 0 4px 12px #00000008;
}

h2 {
  font-size: 21px;
  margin: 0 0 22px;
}

h3 {
  font-size: 16px;
  margin: 22px 0 12px;
}

.field {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
  margin-bottom: 12px;
  font-size: 14px;
}

input[type='color'] {
  width: 45px;
  height: 32px;
  padding: 2px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background: white;
  cursor: pointer;
}

.range-field {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 18px;
  font-size: 14px;
}

input[type='range'] {
  width: 100%;
  accent-color: #4263eb;
  cursor: pointer;
}

select {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 7px;
  background: white;
}

.reset {
  width: 100%;
  margin-top: 25px;
  padding: 12px;
  border: none;
  border-radius: 7px;
  background: #243047;
  color: white;
  cursor: pointer;
}

.reset:hover {
  background: #374967;
}
</style>
