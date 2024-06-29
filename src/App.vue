<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
import FooterV from './components/FooterV.vue';
import WatchOneObserver from './waches/WatchOneObserver.vue';
import WatchMultiObservers from './waches/WatchMultiObservers.vue';
import WatchImmediate from './waches/WatchImmediate.vue';
import WatchOnce from './waches/WatchOnce.vue';
import watchEffectBasic from './watchEffect/watchEffectBasic.vue';
import watchPostEffectBasic from './watchEffect/watchPostEffectBasic.vue';
</script>

<template>
  <HelloWorld msg="Vite + Vue" />
  <p>
    los watches se llama después de que se actualice el componente principal (si
    corresponde) y antes de que se actualice el DOM del componente propietario
  </p>
  <h2>watch one observer</h2>
  <WatchOneObserver />
  <h2>watch multiple observers</h2>
  <WatchMultiObservers />
  <h2>watch inmediate</h2>
  <WatchImmediate />
  <h2>watch once</h2>
  <WatchOnce />
  <h2>watchEffect</h2>
  <watchEffectBasic />
  <h2>watchPostEffect</h2>
  <watchPostEffectBasic />
  <br />
  <FooterV />
</template>

<style scoped></style>
