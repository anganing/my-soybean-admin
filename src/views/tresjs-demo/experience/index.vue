<script setup lang="ts">
import { TresCanvas } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';
</script>

<template>
  <TresCanvas clear-color="#82DBC5">
    <TresPerspectiveCamera :position="[4, 4, 4]" :look-at="[0, 1, 0]" />
    <OrbitControls />
    <TresMesh :position="[0, 1, 0]" :scale="[2, 0.5, 1]" :rotate-x="Math.PI / 4">
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshNormalMaterial />
    </TresMesh>
    <TresMesh>
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshNormalMaterial />
    </TresMesh>
    <TresAxesHelper />
    <TresDirectionalLight :position="[-1, 2, 4]" />
  </TresCanvas>
</template>

<style scoped></style>
