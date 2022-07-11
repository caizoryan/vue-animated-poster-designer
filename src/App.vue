<script setup>
import canvasComponent from './components/canvasComponent.vue'
import controlsComponent from './components/controlsComponent.vue'
import { ref, reactive, provide } from 'vue'
const texts = reactive([{ id: 0, text: 'header', tracking: 5, fontSize: 50, lineSpacing: 50, weight: 900, top: 200, left: 200 }])
var totalElements = ref(0)
const cur = ref(0)
function updateCur (number) {
  cur.value = number
}
provide('textBoxes', texts)
provide('currentElement', cur)
provide('updateCur', updateCur)
provide('addElement', addElement)
function changeValues (values) {
  texts[cur].tracking = values.tracking
  texts[cur].fontSize = values.fontSize
}
function addElement () {
  totalElements.value++
  texts.push({ id: totalElements.value, text: 'newText' + totalElements.value, tracking: 1, fontSize: 50, lineSpacing: 50, weight: 500, top: texts[totalElements.value - 1].top + 100, left: 250 })
}
</script>

<template>
<link rel="stylesheet" href="https://use.typekit.net/qes7oea.css">
<div class="top-border"></div>
<div class="controls-left"></div>
<canvasComponent :textBoxes="texts"/>
<controlsComponent @values="(n) => changeValues(n)"/>
</template>

<style lang="scss">
#app {
  font-family: acumin-pro, sans-serif;
  margin: 0;
  display: flex;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.controls-left{
  z-index: 2;
  width: 50px;
  background-color: white;
}

.top-border{
  position: absolute;
  height: 50px;
  background-color: white;
  width: 100vw;
  z-index: 99;
}
</style>
