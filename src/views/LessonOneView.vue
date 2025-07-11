<template>
  <div class="max-w-3xl mx-auto text-gray-100">
    <h1 class="text-3xl font-bold mb-6 text-red-500 tracking-widest">Lesson 1: Checklist</h1>

    <p>
      Your first lesson is to make a simple text-based adventure game. The story can be anything you
      like, but it should incorporate:
    </p>

    <ul class="space-y-4 mt-5">
      <li
        v-for="(item, index) in checklist"
        :key="index"
        class="flex items-start bg-gray-800 p-4 rounded-lg border border-gray-700"
      >
        <input
          :id="`checkbox-${index}`"
          type="checkbox"
          v-model="item.checked"
          class="w-6 h-6 accent-red-600 focus:ring-2 focus:ring-red-400 rounded-sm mr-4 shrink-0"
        />
        <label
          :for="`checkbox-${index}`"
          class="text-lg text-gray-200 font-mono select-none cursor-pointer"
        >
          ✔️ {{ item.text }}
        </label>
      </li>
    </ul>

    <!-- Congratulations Message -->
    <div
      v-if="allChecked"
      class="mt-8 p-6 bg-green-800 text-green-200 rounded-lg border border-green-600 font-bold text-xl text-center shadow-lg"
    >
      🎉 Lesson Complete: Congratulations, Sam! 🎉<br />
      You've completed all objectives for Lesson 1.
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const checklist = ref([
  { text: 'The game has a Beginning, Middle, and End', checked: false },
  {
    text: 'The game has an item that the player can pick up, which affects the future of the story',
    checked: false,
  },
  {
    text: 'The game is implemented in the console, using `Console.ReadLine();` for player input',
    checked: false,
  },
  {
    text: "The game shows the player's input within the story",
    checked: false,
  },
])

const allChecked = computed(() => checklist.value.every((item) => item.checked))
</script>

<style scoped></style>
