<script setup lang="ts">
import CheckBox from './CheckBox.vue'

defineProps<{
  title: string
  subTitle: string
  isChecked: boolean
}>()

const emit = defineEmits<{
  (e: 'handle-on-press'): void
}>()

// Émettre l'événement au clic
const handleClick = () => {
  emit('handle-on-press')
}
</script>

<template>
  <div class="todoItem" @click="handleClick">
    <div>
      <CheckBox :handle-on-press="() => console.log('pressed')" :is-checked="isChecked" />
    </div>
    <div>
      <h3>{{ title }}</h3>
      <p>{{ subTitle }}</p>
    </div>
  </div>
</template>

<style scoped>
.todoItem {
  display: flex;
  align-items: center;
  cursor: pointer;
  gap: 20px;
}

input[type='checkbox'] {
  margin-right: 1rem;
}

h3 {
  margin: 0;
  font-size: 1rem;
}

p {
  font-size: 0.9rem;
  color: var(--color-subtext);
}
</style>
