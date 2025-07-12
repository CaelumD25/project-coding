<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'

const isMobile = () => {
  return window.innerWidth < 480
}

const showSide = ref(!isMobile())

const toggleSide = () => {
  showSide.value = !showSide.value
}
</script>

<style scoped>
#close-button.open {
  position: absolute;
  top: 10px;
  left: 230px;
}
#close-button.close {
  position: absolute;
  top: 10px;
  left: 0px;
}
.menu-button {
  width: 40px;
  height: 40px;
  background: rgba(30, 41, 57, 0.9);
  border-radius: 2px;
  align-items: center;
  display: flex;
  color: rgb(251, 44, 54, 0.9);
  font-size: 30px;
  padding: 10px;
}
</style>

<template>
  <div class="h-screen bg-gray-900 text-gray-100 font-mono">
    <div class="flex h-full">
      <!-- Sidebar -->
      <button
        id="close-button"
        @click="toggleSide"
        v-bind:class="{ open: !showSide, close: showSide }"
      >
        <div v-if="showSide" class="menu-button">></div>
        <div v-else class="menu-button"><</div>
      </button>

      <aside
        v-if="!showSide"
        class="bg-gray-800 border-r border-gray-700 px-4 py-10"
        style="width: 230px"
      >
        <h1 class="text-xl font-bold text-red-500 mb-6 tracking-widest">Project Code</h1>
        <nav class="space-y-4">
          <RouterLink
            to="/"
            class="block hover:bg-gray-700 px-3 py-2 rounded transition"
            active-class="bg-gray-700 text-white font-semibold"
          >
            Home
          </RouterLink>
          <RouterLink
            to="/1"
            class="block hover:bg-gray-700 px-3 py-2 rounded transition"
            active-class="bg-gray-700 text-white font-semibold"
          >
            📁 Lesson One
          </RouterLink>
        </nav>
      </aside>

      <!-- Main content -->
      <main class="flex-1 overflow-y-auto p-6">
        <RouterView />
      </main>
    </div>
  </div>
</template>
