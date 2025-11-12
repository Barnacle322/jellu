<script setup>
import { RouterView } from 'vue-router'
import AddToMetaMask from './components/AddToMetaMask.vue'
</script>

<template>
    <div class="min-h-screen bg-[#0E181E] text-white">
        <AddToMetaMask />
        <RouterView />
    </div>
</template>
