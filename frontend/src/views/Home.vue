<template>
  <div class="home-container">
    <!-- Top Navigation Bar -->
    <nav class="navbar">
      <div class="nav-brand">
        <img :src="horizontalLogo" alt="SENTRY" class="nav-logo" />
      </div>
      <div class="nav-actions">
        <button class="theme-toggle" @click="emit('toggle-theme')" :title="'Switch to ' + (theme === 'light' ? 'dark' : 'light') + ' mode'">
          <svg v-if="theme === 'light'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="theme-icon">
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
          </svg>
          <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="theme-icon">
            <circle cx="12" cy="12" r="5"></circle>
            <line x1="12" y1="1" x2="12" y2="3"></line>
            <line x1="12" y1="21" x2="12" y2="23"></line>
            <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
            <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
            <line x1="1" y1="12" x2="3" y2="12"></line>
            <line x1="21" y1="12" x2="23" y2="12"></line>
            <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
            <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
          </svg>
        </button>
      </div>
    </nav>

    <div class="main-content">
      <!-- Upper Part: Hero Section -->
      <section class="hero-section">
        <div class="tactical-grid"></div>
        <div class="hero-content">
          <div class="tactical-header">
            <span class="tac-code">SYST: SENTRY_CORE_v7.4</span>
            <span class="tac-sep">|</span>
            <span class="tac-status">LIVE_ENGAGEMENT_ACTIVE</span>
            <span class="tac-sep">|</span>
            <span class="tac-time">{{ new Date().toISOString() }}</span>
          </div>
          
          <h1 class="main-title">
            Master the Variables.<br>
            <span class="gradient-text">Dictate the Outcome.</span>
          </h1>
          
          <div class="hero-desc">
            <p class="subtitle-text">High-Fidelity Strategic Wargaming & Multi-Agent Consequence Assessment.</p>
            <p>
              Sentry orchestrates a <span class="highlight-orange">million parallel strategic actors</span> to decipher unstructured intelligence. Map the global battlefield and discover <span class="highlight-code">optimal outcome paths</span> through sovereign-grade multi-agent simulation.
            </p>
          </div>
          
          <div class="hero-footer">
            <span class="slogan-text">Superior Intelligence. Absolute Clarity.</span>
            <div class="decoration-line"></div>
          </div>
        </div>
      </section>

      <!-- Lower Part: Two-column Layout -->
      <section class="dashboard-section">
        <!-- Left Column: Status and Steps -->
        <div class="left-panel">
          <div class="panel-header">
            <span class="status-dot">■</span> System Status
          </div>
          
          <h2 class="section-title">Wargaming System Ready</h2>
          <p class="section-desc">
            The prediction engine is on standby. Input strategic intelligence datasets to initialize the battlefield simulation sequence.
          </p>
          
          <!-- Metrics Cards -->
          <div class="metrics-row">
            <div class="metric-card">
              <div class="metric-value">Low Cost</div>
              <div class="metric-label">Average $5 per regular simulation</div>
            </div>
            <div class="metric-card">
              <div class="metric-value">High Fidelity</div>
              <div class="metric-label">Simulations with up to a million Actors</div>
            </div>
          </div>

          <!-- Project simulation steps introduction (New area) -->
          <div class="steps-container">
            <div class="steps-header">
               <span class="diamond-icon">◇</span> Prediction Lifecycle
            </div>
            <div class="workflow-list">
              <div class="workflow-item">
                <span class="step-num">01</span>
                <div class="step-info">
                  <div class="step-title">Graph Intelligence</div>
                  <div class="step-desc">Intelligence input extraction & strategic actor memory mapping & GraphRAG battlefield construction</div>
                </div>
              </div>
              <div class="workflow-item">
                <span class="step-num">02</span>
                <div class="step-info">
                  <div class="step-title">Environment Setup</div>
                  <div class="step-desc">Entity relationship extraction & persona generation & environment configuration Agent injecting simulation parameters</div>
                </div>
              </div>
              <div class="workflow-item">
                <span class="step-num">03</span>
                <div class="step-info">
                  <div class="step-title">Combat Simulation</div>
                  <div class="step-desc">Parallel wargaming across multi-platform simulations & automatic parsing of strategic requirements & dynamic temporal updates</div>
                </div>
              </div>
              <div class="workflow-item">
                <span class="step-num">04</span>
                <div class="step-info">
                  <div class="step-title">Report Generation</div>
                  <div class="step-desc">ReportAgent has a rich set of tools to interact deeply with the post-simulation environment</div>
                </div>
              </div>
              <div class="workflow-item">
                <span class="step-num">05</span>
                <div class="step-info">
                  <div class="step-title">Deep Interaction</div>
                  <div class="step-desc">Chat with anyone in the simulated world & chat with ReportAgent</div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column: Interaction Console -->
        <div class="right-panel">
          <div class="console-box">
            <!-- Upload Section -->
            <div class="console-section">
              <div class="console-header">
                <span class="console-label">01 / Intelligence Inputs</span>
                <span class="console-meta">Strategic Briefings: PDF, MD, TXT</span>
              </div>
              
              <div 
                class="upload-zone"
                :class="{ 'drag-over': isDragOver, 'has-files': files.length > 0 }"
                @dragover.prevent="handleDragOver"
                @dragleave.prevent="handleDragLeave"
                @drop.prevent="handleDrop"
                @click="triggerFileInput"
              >
                <input
                  ref="fileInput"
                  type="file"
                  multiple
                  accept=".pdf,.md,.txt"
                  @change="handleFileSelect"
                  style="display: none"
                  :disabled="loading"
                />
                
                <div v-if="files.length === 0" class="upload-placeholder">
                  <div class="upload-icon">↑</div>
                  <div class="upload-title">Drag and drop files to upload</div>
                  <div class="upload-hint">Or click to browse file system</div>
                </div>
                
                <div v-else class="file-list">
                  <div v-for="(file, index) in files" :key="index" class="file-item">
                    <span class="file-icon">📄</span>
                    <span class="file-name">{{ file.name }}</span>
                    <button @click.stop="removeFile(index)" class="remove-btn">×</button>
                  </div>
                </div>
              </div>
            </div>

            <!-- Divider -->
            <div class="console-divider">
              <span>Input Parameters</span>
            </div>

            <!-- Input Area -->
            <div class="console-section">
              <div class="console-header">
                <span class="console-label">>_ 02 / Strategic Objective</span>
              </div>
              <div class="input-wrapper">
                <textarea
                  v-model="formData.simulationRequirement"
                  class="code-input"
                  placeholder="// Enter strategic objectives or tactical requirements (e.g., 'Predict the geopolitical consequences if the trade agreement is unilaterally terminated next quarter.')"
                  rows="6"
                  :disabled="loading"
                ></textarea>
                <div class="model-badge">Engine: Sentry-V1.0</div>
              </div>
            </div>

            <!-- Start Button -->
            <div class="console-section btn-section">
                <button 
                class="start-engine-btn"
                @click="startSimulation"
                :disabled="!canSubmit || loading"
              >
                <span v-if="!loading">Execute Wargame</span>
                <span v-else>Mobilizing...</span>
                <span class="btn-arrow">→</span>
              </button>
            </div>
          </div>
        </div>
      </section>

      <!-- Historical Project Database -->
      <HistoryDatabase />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'
import HistoryDatabase from '../components/HistoryDatabase.vue'

const props = defineProps({
  theme: String
})

const emit = defineEmits(['toggle-theme'])

const router = useRouter()

// Theme-aware assets
const horizontalLogo = computed(() => {
  return new URL(`../assets/logo/horizontal_${props.theme === 'light' ? 'dark' : 'light'}.png`, import.meta.url).href
})

const heroLogo = computed(() => {
  return new URL(`../assets/logo/logo_${props.theme === 'light' ? 'dark' : 'light'}.png`, import.meta.url).href
})

// Form data
const formData = ref({
  simulationRequirement: ''
})

// File list
const files = ref([])

// Status
const loading = ref(false)
const error = ref('')
const isDragOver = ref(false)

// File input reference
const fileInput = ref(null)

// Computed property: whether it can be submitted
const canSubmit = computed(() => {
  return formData.value.simulationRequirement.trim() !== '' && files.value.length > 0
})

// Trigger file selection
const triggerFileInput = () => {
  if (!loading.value) {
    fileInput.value?.click()
  }
}

// Handle file selection
const handleFileSelect = (event) => {
  const selectedFiles = Array.from(event.target.files)
  addFiles(selectedFiles)
}

// Handle drag and drop related
const handleDragOver = (e) => {
  if (!loading.value) {
    isDragOver.value = true
  }
}

const handleDragLeave = (e) => {
  isDragOver.value = false
}

const handleDrop = (e) => {
  isDragOver.value = false
  if (loading.value) return
  
  const droppedFiles = Array.from(e.dataTransfer.files)
  addFiles(droppedFiles)
}

// Add files
const addFiles = (newFiles) => {
  const validFiles = newFiles.filter(file => {
    const ext = file.name.split('.').pop().toLowerCase()
    return ['pdf', 'md', 'txt'].includes(ext)
  })
  files.value.push(...validFiles)
}

// Remove file
const removeFile = (index) => {
  files.value.splice(index, 1)
}

// Scroll to bottom
const scrollToBottom = () => {
  window.scrollTo({
    top: document.body.scrollHeight,
    behavior: 'smooth'
  })
}

// Start simulation - Redirect immediately, API call handled on Process page
const startSimulation = () => {
  if (!canSubmit.value || loading.value) return
  
  // Store data to be uploaded
  import('../store/pendingUpload.js').then(({ setPendingUpload }) => {
    setPendingUpload(files.value, formData.value.simulationRequirement)
    
    // Redirect to Process page immediately (using a special identifier for new projects)
    router.push({
      name: 'Process',
      params: { projectId: 'new' }
    })
  })
}
</script>

<style scoped>
.home-container {
  min-height: 100vh;
  background: var(--bg);
  color: var(--text);
  transition: background-color 0.3s ease;
}

.home-container::selection {
  background: var(--orange);
  color: var(--white);
}

/* Top Navigation */
.navbar {
  height: 60px;
  background: var(--bg);
  border-bottom: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 40px;
  backdrop-filter: blur(10px);
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-brand {
  height: 32px;
  display: flex;
  align-items: center;
}

.nav-logo {
  height: 100%;
  width: auto;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

.theme-toggle {
  background: var(--gray-light);
  border: 1px solid var(--border);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  transition: all 0.3s ease;
}

.theme-toggle:hover {
  background: var(--border);
  transform: scale(1.1);
}

.theme-icon {
  width: 18px;
  height: 18px;
  color: var(--text);
}

.arrow {
  display: inline-block;
  margin-left: 8px;
}

/* Main Content Area */
.main-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 60px 40px;
}

/* Hero Section */
.hero-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 60px 0 100px 0;
  margin-bottom: 80px;
  position: relative;
  overflow: hidden;
  background: radial-gradient(circle at 50% 50%, var(--bg-alpha) 0%, transparent 70%);
}

.tactical-grid {
  position: absolute;
  inset: 0;
  background-image: 
    linear-gradient(var(--border) 1px, transparent 1px),
    linear-gradient(90deg, var(--border) 1px, transparent 1px);
  background-size: 40px 40px;
  opacity: 0.03;
  pointer-events: none;
}

.hero-content {
  width: 100%;
  max-width: 1000px;
  position: relative;
  z-index: 2;
}

.tactical-header {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--gray-medium);
  margin-bottom: 24px;
  letter-spacing: 2px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
  opacity: 0.6;
}

.tac-sep {
  opacity: 0.3;
}

.tac-status {
  color: var(--orange);
  font-weight: 700;
}

.tag-row {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 25px;
  font-family: var(--font-mono);
  font-size: 0.8rem;
}

.orange-tag {
  background: var(--orange);
  color: var(--white);
  padding: 4px 10px;
  font-weight: 700;
  letter-spacing: 1px;
  font-size: 0.75rem;
}

.version-text {
  color: #999;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.main-title {
  font-size: 4.8rem;
  line-height: 1.0;
  font-weight: 800;
  margin: 0 0 32px 0;
  letter-spacing: -0.06em;
  color: var(--text);
  animation: reveal-up 1s cubic-bezier(0.16, 1, 0.3, 1);
  text-transform: uppercase;
}

.gradient-text {
  background: linear-gradient(135deg, var(--text) 0%, var(--gray-medium) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
  position: relative;
}

.gradient-text::after {
  content: '';
  position: absolute;
  bottom: 5px;
  left: 0;
  width: 100%;
  height: 4px;
  background: var(--orange);
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.main-title:hover .gradient-text::after {
  transform: scaleX(1);
  transform-origin: left;
}

@keyframes reveal-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.hero-desc {
  max-width: 780px;
  margin: 0 auto 40px auto;
  text-align: center;
}

.subtitle-text {
  font-size: 1.4rem;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 20px;
  letter-spacing: -0.02em;
}

.hero-desc p:not(.subtitle-text) {
  font-size: 1.15rem;
  line-height: 1.6;
  color: var(--gray-text);
  font-weight: 400;
}

.hero-desc p {
  margin-bottom: 1.5rem;
}

.highlight-bold {
  color: var(--text);
  font-weight: 700;
}

.highlight-orange {
  color: var(--orange);
  font-weight: 700;
  font-family: var(--font-mono);
}

.highlight-code {
  background: var(--gray-light);
  padding: 2px 6px;
  border-radius: 2px;
  font-family: var(--font-mono);
  font-size: 0.9em;
  color: var(--text);
  font-weight: 600;
}

.hero-footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.slogan-text {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--text);
  letter-spacing: 4px;
  text-transform: uppercase;
  opacity: 0.8;
}

.decoration-line {
  width: 60px;
  height: 2px;
  background: var(--orange);
}

.blinking-cursor {
  color: var(--orange);
  animation: blink 1s step-end infinite;
  font-weight: 700;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.decoration-square {
  width: 16px;
  height: 16px;
  background: var(--orange);
}

/* Removed hero-right and related styles */

/* Dashboard Two-column Layout */
.dashboard-section {
  display: flex;
  gap: 60px;
  border-top: 1px solid var(--border);
  padding-top: 60px;
  align-items: flex-start;
}

.dashboard-section .left-panel,
.dashboard-section .right-panel {
  display: flex;
  flex-direction: column;
}

/* Left Panel */
.left-panel {
  flex: 0.8;
}

.panel-header {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: #999;
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 20px;
}

.status-dot {
  color: var(--orange);
  font-size: 0.8rem;
}

.section-title {
  font-family: var(--font-sans);
  font-size: 2.2rem;
  font-weight: 800;
  margin: 0 0 15px 0;
  letter-spacing: -0.03em;
}

.section-desc {
  color: var(--gray-text);
  margin-bottom: 25px;
  line-height: 1.6;
}

.metrics-row {
  display: flex;
  gap: 20px;
  margin-bottom: 15px;
}

.metric-card {
  border: 1px solid var(--border);
  padding: 24px 32px;
  flex: 1;
  background: var(--gray-light);
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
  overflow: hidden;
}

.metric-card:hover {
  border-color: var(--orange);
  transform: translateY(-4px);
  background: var(--white);
  box-shadow: 0 10px 30px rgba(255, 77, 0, 0.1);
}

.metric-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: var(--orange);
  transform: translateY(100%);
  transition: transform 0.3s;
}

.metric-card:hover::before {
  transform: translateY(0);
}

.metric-value {
  font-family: var(--font-sans);
  font-size: 2.2rem;
  font-weight: 800;
  margin-bottom: 8px;
  color: var(--text);
  letter-spacing: -0.04em;
}

.metric-label {
  font-size: 0.85rem;
  color: #999;
}

/* Project Simulation Steps Introduction */
.steps-container {
  border: 1px solid var(--border);
  padding: 30px;
  position: relative;
}

.steps-header {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: #999;
  margin-bottom: 25px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.diamond-icon {
  font-size: 1.2rem;
  line-height: 1;
}

.workflow-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.workflow-item {
  display: flex;
  align-items: flex-start;
  gap: 20px;
}

.step-num {
  font-family: var(--font-mono);
  font-weight: 700;
  color: var(--text);
  opacity: 0.3;
}

.step-info {
  flex: 1;
}

.step-title {
  font-family: var(--font-sans);
  font-weight: 700;
  font-size: 1.1rem;
  margin-bottom: 4px;
  letter-spacing: -0.01em;
}

.step-desc {
  font-size: 0.85rem;
  color: var(--gray-text);
}

/* Right Interaction Console */
.right-panel {
  flex: 1.2;
}

.console-box {
  background: var(--card-bg);
  border: 1px solid var(--border);
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.05);
  border-radius: 12px;
  position: relative;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  padding: 15px;
  overflow: hidden;
}

.console-box:hover {
  box-shadow: 0 40px 80px rgba(0,0,0,0.08);
}

.console-box::before {
  content: '';
  position: absolute;
  inset: -1px;
  background: linear-gradient(135deg, var(--orange), transparent, var(--text));
  z-index: -1;
  opacity: 0.1;
  border-radius: inherit;
}

.console-section {
  padding: 20px;
}

.console-section.btn-section {
  padding-top: 0;
}

.console-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 15px;
  font-family: var(--font-mono);
  font-size: 0.75rem;
  color: #666;
}

.upload-zone {
  border: 1px dashed var(--border);
  height: 240px;
  overflow-y: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  background: var(--bg-alpha);
  border-radius: 8px;
}

.upload-zone.has-files {
  align-items: flex-start;
}

.upload-zone:hover {
  background: var(--white);
  border-color: var(--orange);
  box-shadow: inset 0 0 0 1px rgba(255, 77, 0, 0.1);
}

.upload-placeholder {
  text-align: center;
}

.upload-icon {
  width: 40px;
  height: 40px;
  border: 1px solid #DDD;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 15px;
  color: #999;
}

.upload-title {
  font-weight: 500;
  font-size: 0.9rem;
  margin-bottom: 5px;
}

.upload-hint {
  font-family: var(--font-mono);
  font-size: 0.75rem;
  color: #999;
}

.file-list {
  width: 100%;
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.file-item {
  display: flex;
  align-items: center;
  background: var(--white);
  padding: 8px 12px;
  border: 1px solid #EEE;
  font-family: var(--font-mono);
  font-size: 0.85rem;
}

.file-name {
  flex: 1;
  margin: 0 10px;
}

.remove-btn {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
  color: #999;
}

.console-divider {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.console-divider::before,
.console-divider::after {
  content: '';
  flex: 1;
  height: 1px;
  background: #EEE;
}

.console-divider span {
  padding: 0 15px;
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: #BBB;
  letter-spacing: 1px;
}

.input-wrapper {
  position: relative;
  border: 1px solid #DDD;
  background: #FAFAFA;
}

.code-input {
  width: 100%;
  border: none;
  background: var(--bg-alpha);
  padding: 24px;
  font-family: var(--font-mono);
  font-size: 0.95rem;
  color: var(--text);
  line-height: 1.6;
  resize: vertical;
  outline: none;
  min-height: 180px;
}

.model-badge {
  position: absolute;
  bottom: 10px;
  right: 15px;
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: #AAA;
}

.start-engine-btn {
  width: 100%;
  background: var(--orange);
  color: var(--white);
  border: none;
  padding: 24px;
  border-radius: 8px;
  font-family: var(--font-sans);
  font-weight: 700;
  font-size: 1.2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  letter-spacing: 0.5px;
  position: relative;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(255, 77, 0, 0.2);
}

/* Clickable state (non-disabled) */
.start-engine-btn:not(:disabled) {
  background: var(--black);
  border: none;
  box-shadow: 0 10px 20px -5px rgba(0,0,0,0.3);
}

.start-engine-btn:hover:not(:disabled) {
  background: var(--black);
  transform: translateY(-4px) scale(1.01);
  box-shadow: 0 20px 40px -10px rgba(0,0,0,0.4);
}

.start-engine-btn::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 150%;
  height: 150%;
  background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
  transform: translate(-50%, -50%) scale(0);
  transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.start-engine-btn:hover::after {
  transform: translate(-50%, -50%) scale(1);
}

.start-engine-btn:active:not(:disabled) {
  transform: translateY(-2px) scale(0.98);
}

.start-engine-btn:disabled {
  background: #F0F0F0;
  color: #BBB;
  cursor: not-allowed;
  transform: none;
  border: 1px solid #EEE;
}

/* Guide animation: subtle border pulse */
@keyframes pulse-border {
  0% { box-shadow: 0 0 0 0 rgba(0, 0, 0, 0.2); }
  70% { box-shadow: 0 0 0 6px rgba(0, 0, 0, 0); }
  100% { box-shadow: 0 0 0 0 rgba(0, 0, 0, 0); }
}

/* Responsive adaptation */
@media (max-width: 1024px) {
  .dashboard-section {
    flex-direction: column;
  }
  
  .hero-section {
    flex-direction: column;
  }
  
  .hero-left {
    padding-right: 0;
    margin-bottom: 40px;
  }
  
  .hero-logo {
    max-width: 200px;
    margin-bottom: 20px;
  }
}
</style>
