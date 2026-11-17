<template>
  <RouterView />
  <aside v-if="route.name !== 'cross-museum-guide'" class="museum-chat">
    <section
      v-show="chatOpen"
      id="museum-chat-panel"
      class="museum-chat-panel"
      aria-label="線上客服"
    >
      <iframe
        v-if="chatLoaded"
        class="museum-chat-frame"
        src="https://moeai-test.omniguider.com/home/chat/nmns"
        title="線上客服"
        allow="camera; microphone"
        loading="lazy"
      ></iframe>
    </section>
    <button
      class="museum-chat-toggle"
      type="button"
      aria-controls="museum-chat-panel"
      :aria-expanded="chatOpen"
      @click="toggleChat"
    >
      {{ chatOpen ? '收合客服' : '開啟客服' }}
    </button>
  </aside>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'
import { RouterView, useRoute } from 'vue-router'

const route = useRoute()
const chatOpen = ref(false)
const chatLoaded = ref(false)

function toggleChat() {
  chatOpen.value = !chatOpen.value
  if (chatOpen.value) chatLoaded.value = true
}

watch(
  () => route.name,
  (routeName) => {
    if (routeName === 'cross-museum-guide') chatOpen.value = false
  },
)
</script>
