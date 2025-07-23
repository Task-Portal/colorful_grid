<script setup lang="ts">

import { defineProps } from "vue";


const props=defineProps<{
    rows:number
    cols:number
    colors:string[]
}>()

function randomColor(){
    // let colors = ["red", "green", "blue", "orange"]
    const color=props.colors[Math.floor(Math.random()*props.colors.length)]
    return color
}
function randomColorName(){
    const colors = ["красный", "зеленый", "синий", "оранжевый","коричневый","черный"]
    const color=colors[Math.floor(Math.random()*props.colors.length)]
    return color
}
</script>

<template>
    <div class="grid gap-2" :style="{ gridTemplateColumns: `repeat(${cols}, 1fr)` }">
        <div v-for="(_, i) in rows * cols" :key="i" class="p-2 border text-center font-bold rounded shadow"
            :style="{ color: randomColor(), backgroundColor: 'lightblue' }">
            {{ randomColorName().toUpperCase() }}</div>
    </div>
</template>