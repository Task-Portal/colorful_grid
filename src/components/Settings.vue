<template>
    <div class="mb-4">
        <label class="block mb-1">Grid Size:</label>
        <input type="number" v-model.number="rows" class="mr-2 p-1 border" min="1" />
        x
        <input type="number" v-model.number="cols" class="ml-2 p-1 border" min="1">
        <label class="block mt-2 mb-1">Colors (comma-separated):</label>
        <input v-model="colorString" class="p-1 border w-full" />

        <button @click="apply" class="mt-2 px-3 py-1 bg-green-500 text-white rounded-2xl">
            Apply Settings
        </button>
    </div>
</template>

<script setup lang="ts">
import {ref} from "vue"

const emit=defineEmits(['settings-changed'])

const rows=ref(6)
const cols=ref(6)
const colorString=ref('красный,зеленый,синий,оранжевый,коричневый,черный')

function apply(){
    const colors=colorString.value.split(",").map(c=>c.trim())
    emit('settings-changed', {rows: rows.value, cols:cols.value, colors})
}
</script>