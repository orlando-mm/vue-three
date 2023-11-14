<script setup lang="ts">
import {useRenderLoop} from "@tresjs/core";
import {ref} from "vue";

const {onLoop} = useRenderLoop()

const rotationY = ref(0)
const rotationZ = ref(0)

onLoop(() => {
  rotationY.value += 0.01
  rotationY.value += 0.02
})
</script>

<template>
  <TresCanvas clear-color="#2B3846">
    <TresPerspectiveCamera/>
    <TresScene>
      <TresMesh :position="[0, 0, 0]" :rotation="[0, rotationY, rotationZ]">
        <TresBoxGeometry/>
        <TresMeshNormalMaterial/>
      </TresMesh>
    </TresScene>
  </TresCanvas>
</template>

<style scoped>

</style>