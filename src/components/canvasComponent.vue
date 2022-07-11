<template>
<div class="canvas">
    <textComponent v-for="text in props.textBoxes"
    :key="text.id"
    :id="text.id"
    :class="'text'+text.id"
    :fontSize="text.fontSize"
    :lineSpacing="text.lineSpacing"
    :tracking="text.tracking"
    :weight = "text.weight"
    :left="text.left"
    :top="text.top"
    :text="text.text"
    />
</div>
</template>

<script setup>
import textComponent from './textComponent.vue'
import { defineProps } from 'vue'
const props = defineProps(['textBoxes'])
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.canvas{
  padding-bottom: 0;
  margin-bottom: 0;
  margin-top: 50px;
  overflow: hidden;
  background-color: black;
  width: 500px;
  height: 600px;
  border: 1px black solid;
}
</style>
