<template>
  <div :class="['app-wrapper', theme + '-theme']">
    <router-view :theme="theme" @toggle-theme="toggleTheme" />
  </div>
</template>

<script setup>
import { ref, onMounted, provide } from 'vue'

const theme = ref(localStorage.getItem('sentry-theme') || 'light')

const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  localStorage.setItem('sentry-theme', theme.value)
}

provide('theme', theme)
provide('toggleTheme', toggleTheme)
</script>

<style>
/* Global style reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  /* Brand Colors */
  --orange: #FF4D00;
  --accent: #FF6B35;
  --white: #FFFFFF;
  --black: #000000;
  
  /* Typography */
  --font-mono: 'JetBrains Mono', monospace;
  --font-sans: 'DM Sans', 'Noto Sans SC', system-ui, sans-serif;

  /* Default (Light) Theme Variables */
  --bg: #FFFFFF;
  --text: #050505;
  --dashboard-bg: #111111;
  --dashboard-text: #E5E5E5;
  --gray-dark: #1A1A1A;
  --gray-medium: #4A4A4A;
  --gray-light: #F8F9FA;
  --gray-text: #606060;
  --border: #EEEEEE;
  --header-bg: rgba(255, 255, 255, 0.8);
  --glass: rgba(255, 255, 255, 0.8);
  --card-bg: #FFFFFF;
  --shadow: 0 4px 12px rgba(0, 0, 0, 0.05);

  /* Graph Colors */
  --graph-link: #C0C0C0;
  --graph-link-active: #3498db;
  --graph-label-bg: rgba(255, 255, 255, 0.95);
  --graph-label-text: #666;
  --graph-node-stroke: #FFFFFF;
  --graph-node-label: #333;
}

.dark-theme {
  --bg: #050505;
  --text: #FFFFFF;
  --dashboard-bg: #050505;
  --dashboard-text: #FFFFFF;
  --gray-dark: #F8F9FA;
  --gray-medium: #A0A0A0;
  --gray-light: #1A1A1A;
  --gray-text: #B0B0B0;
  --border: #222222;
  --header-bg: rgba(5, 5, 5, 0.8);
  --glass: rgba(10, 10, 10, 0.8);
  --card-bg: #111111;
  --shadow: 0 4px 20px rgba(0, 0, 0, 0.3);

  /* Graph Colors */
  --graph-link: #444444;
  --graph-link-active: #FF4D00;
  --graph-label-bg: rgba(20, 20, 20, 0.95);
  --graph-label-text: #BBBBBB;
  --graph-node-stroke: #050505;
  --graph-node-label: #EEEEEE;
}

.app-wrapper {
  min-height: 100vh;
  background-color: var(--bg);
  color: var(--text);
  transition: background-color 0.3s ease, color 0.3s ease;
}

#app {
  font-family: var(--font-sans);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Scrollbar styles */
::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

::-webkit-scrollbar-track {
  background: var(--bg);
}

::-webkit-scrollbar-thumb {
  background: var(--gray-medium);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: var(--orange);
}

/* Global button styles */
button {
  font-family: inherit;
  transition: all 0.2s cubic-bezier(0.16, 1, 0.3, 1);
}

/* Transitions */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
