<script setup lang="ts">
import { type Ref, ref, watch, reactive } from 'vue';

const checkImput: Ref<boolean> = ref(false);
const form: {confirm: bollean} = reactive({
  confirm: false
})
const name: Ref<String> = ref('')

   // aqui podemos hacer [checkImput.value , form.confirm ], pero se ejecutarioa mas segido( cada que cualquiera de los d2 se modifique)
   // hacerlo asi checkImput.value && form.confirm  se va hacer la operacion y cuando cambie el valor de la OPERACION silo ahi se ejecuta
watch(
()=> checkImput.value && form.confirm // observamos varios elementos reactivos
, async (newQuestion, oldQuestion)=> {
  console.log('new value',newQuestion)
  console.log('old value',oldQuestion)

  if(checkImput.value && form.confirm) {
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
  <input type="checkbox" v-model='form.confirm' >
  confirmar
</input>
<br/>
<input v-model='name' />



</template>

<style scoped></style>
