<script setup lang="ts">
import { type Ref, ref, watchPostEffect, watch, watchEffect } from 'vue';

const input: Ref<number> = ref(1);

// podemos acceder al DOM actualizado
watchPostEffect(() => {
  input.value;
  const element = document.getElementById('p');
  console.log('watchPostEffect', element.innerHTML);
});

// No podemos acceder la DOM actualizado por defecto
watch(
  input,
  () => {
    const element = document.getElementById('p');
    console.log('watch', element.innerHTML);
  }
  // { flush: 'post' } // con esta podemos aceder al Dom actualizado
);

// No podemos acceder la DOM actualizado por defecto
watchEffect(
  () => {
    input.value;
    const element = document.getElementById('p');
    console.log('watchEffect', element?.innerHTML);
  }
  // { flush: 'post' } // con esta podemos aceder al Dom actualizado
);
</script>

<template>
  <input id="id" type="number" v-model="input" />
  <p id="p">mi texto: {{ input }}</p>
</template>

<style scoped></style>
