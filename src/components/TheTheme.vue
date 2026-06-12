<script setup lang="ts">
import { ref } from "vue"
import { SparklesIcon } from "@heroicons/vue/24/outline"
import VButton from "./ui/VButton.vue"

const root = document.documentElement
const isDark = ref(root.classList.contains("dark"))

function toggleTheme() {
    isDark.value = !isDark.value
    root.classList.toggle("dark", !isDark.value)
}
</script>

<template>
    <VButton @click="toggleTheme" size="icon-sm" title="Theme">
        <SparklesIcon class="stroke-1.25" />
    </VButton>
</template>
