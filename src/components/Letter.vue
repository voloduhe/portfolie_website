<script setup>
import {
  Camera,
  Renderer,
  Scene,
  GltfModel,
  AmbientLight
} from 'troisjs';
import { onMounted, onUnmounted, ref } from 'vue';

const renderer = ref(null)
const letter = ref(null)
const yRotation = ref(1.2)
const interv = ref(null)

function runRotation() {
  interv.value = setInterval(() => {
    yRotation.value -= 0.005
  }, 1000 / 60)
}


onMounted(() => {
  runRotation()
})

onUnmounted(() => {
  clearInterval(interv.value)
})

function onReady() {

}

</script>

<template>
  <Renderer ref="renderer" resize="true" antialias class="cans">
    <Camera :position="{ z: 10 }" />
    <Scene background="#161719">
      <AmbientLight :intensity="1" />
      <GltfModel :rotation="{ x: 0.3, y: yRotation, z: 0 }" :scale="{ x: 1.45, y: 1.45, z: 1.45 }"
        :position="{ x: 0, y: -1.6, z: 0 }" ref="letter" src="/src/models/v_letter.gltf" @load="onReady" />
    </Scene>
  </Renderer>
</template>

<style scoped lang="sass">
.cans
  width: 100%
  height: 100%

</style>
