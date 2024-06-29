<script setup lang="ts">
import { type Ref, ref, watch } from 'vue';

const checkImput: Ref<boolean> = ref(false);

watch(checkImput, async (newQuestion, oldQuestion)=> {
  alert('ejecucion imediata')
  },
//{ immediate: true } // se ejecuta inmediatamente cuando se crea el componente y de aqui en adelente cada que se modifique el elemento reactivo
);

</script>

<template>
  <input type="checkbox" v-model='checkImput' >
  ejecucion imediata
</input>
<br/>


</template>

<style scoped></style>
