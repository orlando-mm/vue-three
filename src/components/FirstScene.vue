<script setup lang="ts">
import {useRenderLoop} from "@tresjs/core";
import {ref, shallowRef} from "vue";

const {onLoop} = useRenderLoop()

const torusRef = shallowRef()
const torusPosition = ref([0, 0, 0])

onLoop(({delta}) => {
  if (!torusRef?.value) return
  torusRef.value.rotation.x += delta
  torusRef.value.rotation.y += delta
})
</script>

<template>
  <TresCanvas window-size clear-color="#2B3846">
    <TresPerspectiveCamera :args="[75, 1, 0.1, 1000]" :position="[3, 1, 4]" :look-at="[0, 0, 0]"/>
    <TresMesh ref="torusRef" :position="torusPosition">
      <TresTorusKnotGeometry :args="[1, 0.4, 100, 16]"/>
      <TresMeshNormalMaterial/>
    </TresMesh>
    <TresGridHelper/>
    <TresAxesHelper :scale="[3, 3, 3]"/>
  </TresCanvas>
</template>

<style scoped>

</style>