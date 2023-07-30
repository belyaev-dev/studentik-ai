<template>
  <div>
    <button class="chat-opener" @click="toggleChat">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="30"
        height="30"
        viewBox="0 0 800 800"
      >
        <circle cx="400" cy="400" r="400" fill="#0099cc" />
        <path
          d="M300 200h200a100 100 0 0 1 100 100v200a100 100 0 0 1-100 100h-50l-50 100v-100h-100a100 100 0 0 1-100-100v-200a100 100 0 0 1 100-100z"
          fill="white"
        />
      </svg>
    </button>
    <iframe
      v-if="isChatOpen"
      ref="chatIframe"
      src="/chat.html"
      width="300"
      height="400"
    ></iframe>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isChatOpen: false,
    };
  },
  methods: {
    toggleChat() {
      this.isChatOpen = !this.isChatOpen;
    },
  },
};
</script>

<style>
.chat-opener {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}
</style>
