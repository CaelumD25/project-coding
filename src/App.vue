<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="h-screen bg-gray-900 text-gray-100 font-mono">
    <div class="flex h-full">
      <!-- Sidebar -->
      <aside class="w-64 bg-gray-800 border-r border-gray-700 px-4 py-6">
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
