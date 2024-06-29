<script setup lang="ts">
import { type Ref, ref, watchEffect } from 'vue';

const todoId: Ref<number> = ref(1);
const data: Ref<object> = ref(null);

// el watchEffect tiene implicitamente el { immediate: true }
// el watchEffect no necesita una lista de dependencias reactivas explicita
// en su logar escucha las dependencias en la logica (como computed)
// watchEffect puede ser una mejor opcion que utlizar un watche con  { deep: true }
watchEffect(async () => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  );
  data.value = await response.json();
});
</script>

<template>
  <input type="number" v-model.number="todoId" />
  <p>{{ data }}</p>
  <br />
</template>

<style scoped></style>
