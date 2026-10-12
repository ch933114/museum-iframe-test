<template>
  <RouterView />
  <iframe
    v-if="route.name !== 'cross-museum-guide'"
    class="museum-chat-frame"
    src="https://moeai-test.omniguider.com/home/chat/nmns"
    title="線上客服"
    allow="camera; microphone"
    loading="lazy"
  ></iframe>
</template>

<script setup lang="ts">
import { RouterView, useRoute } from 'vue-router'

const route = useRoute()
</script>
