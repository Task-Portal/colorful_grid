<script setup lang="ts">
import ColorGrid from "./components/ColorGrid.vue"
import Timer from "./components/Timer.vue"
import Settings from "./components/Settings.vue"
import {ref} from "vue"

const rows=ref(6)
const cols=ref(6)
const colors=ref(["red", "green", "blue", "orange","brown","black"])

function updateSettings(newSettings:{rows:number; cols:number; colors:string[]}){
  rows.value=newSettings.rows
  cols.value=newSettings.cols
  colors.value = newSettings.colors
}

 function saveTime(time:number){
  // await fetch("http:/localhost:5000/api/timer",{
  //   method:"POST", headers:{"Content-Type":"application/json"},
  //   body:JSON.stringify({duration:time})
  // })

  console.log(time)
}


</script>

<template>
<div class="min-h-screen bg-gray-100 p-4">
<h1 class="text-2xl font-bold mb-4">Color Grid Test</h1>
<Settings @settings-changed="updateSettings"/>
<Timer @finished="saveTime"/>
<ColorGrid :rows="rows" :cols="cols" :colors="colors"/>
</div>
</template>

