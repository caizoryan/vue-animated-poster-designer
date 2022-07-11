<template>
    <h1 contenteditable="true" @click="funyboi" v-bind:class="props.class"
    v-bind:style="{
        fontSize: + props.fontSize + 'px',
        letterSpacing: + props.tracking + 'px',
        fontWeight: + props.weight,
        lineHeight: + props.lineSpacing + 'px',
        top: + props.top + 'px',
        left: + props.left + 'px'
    }">{{ props.text }}</h1>
</template>

<script setup>
import { defineProps, inject, onMounted } from 'vue'
const props = defineProps(['id', 'text', 'class', 'tracking', 'fontSize', 'weight', 'top', 'left', 'lineSpacing'])
var id = 0
const updateCur = inject('updateCur')

onMounted(() => {
  id = props.id
})

function funyboi () {
  updateCur(id)
}
</script>

<style scoped lang="scss">

*{
    position: absolute;
    top: 50px;
    left: 100px;
    color: white;
    margin: 0;
    padding: 0;
    &:focus-visible{
        border: 1px white solid;
        outline: 1px white solid;
    }
}
</style>
