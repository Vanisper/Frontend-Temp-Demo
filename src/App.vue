<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import ModelPopup from './components/ModelPopup.vue'

import { ref } from 'vue'

const showPopup = ref(false)

const onPopupConfirm = () => {
  console.log('Popup confirmed')
  showPopup.value = false
}

const onPopupCancel = () => {
  console.log('Popup canceled')
  showPopup.value = false
}

const onPopupClose = () => {
  console.log('Popup closed')
  showPopup.value = false
}

</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
  <ModelPopup
    :show="showPopup"
    title="Popup Title"
    message="Popup Message"
    confirmText="Confirm"
    cancelText="Cancel"
    @onCancel="onPopupCancel"
    @onConfirm="onPopupConfirm"
    @onClose="onPopupClose"
  />
  <button @click="showPopup = true">Show Popup</button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
