<script setup lang="ts">
import TheHeader from "./components/layout/TheHeader.vue"
</script>

<template>
    <div class="space-y-5.75">
        <TheHeader />
        <RouterView />
    </div>
</template>
