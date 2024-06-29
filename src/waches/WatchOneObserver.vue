<script setup lang="ts">
import { type Ref, ref, watch } from 'vue';

const checkImput: Ref<boolean> = ref(false);
const name: Ref<String> = ref('')

  // solo observamos un elemento reactivo
watch(checkImput, async (newQuestion, oldQuestion)=> {
  console.log('new value',newQuestion)
  console.log('old value',oldQuestion)

  if(checkImput.value){
    name.value = 'loading....'

    const res = await fetch('https://randomuser.me/api/?nat=us&randomapi');
    const data = await res.json()
    const nameData = data?.results?.[0]?.name?.first

    name.value = nameData;
  }
});

</script>

<template>
  <input type="checkbox" v-model='checkImput' >
  nombre aleatorio
</input>
<br/>
<input v-model='name' />


</template>

<style scoped></style>
