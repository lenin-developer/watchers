<script setup lang="ts">
import { type Ref, ref, watch } from 'vue';

const checkImput: Ref<boolean> = ref(false);

  // solo observamos un elemento
watch(checkImput, async (newQuestion, oldQuestion)=> {
  alert('ejecucion una sola vez (la primera ves que se modifica el valor reactivo)')
  },
{ once: true }
);

</script>

<template>
  <input type="checkbox" v-model='checkImput' >
  se ejeucta solo una vez
</input>
<br/>


</template>

<style scoped></style>
