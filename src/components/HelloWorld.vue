<script setup lang="ts">
import { ref } from "vue";

const yesImg = ref(new URL("@/assets/together.jpg", import.meta.url).href);
const beautyImg = ref(new URL("@/assets/beauty.jpg", import.meta.url).href);
</script>

<template>
  <div class="w-full h-screen bg-pink-200">
    <p class="text-center text-6xl">Will you be my valentine</p>
    <div class="mx-auto w-64 h-64 border-2 border-black overflow-hidden mt-10">
      <img
        :src="beautyImg"
        alt="example"
        class="w-full h-full object-cover object-center"
      />
    </div>

    <div class="flex justify-center gap-4 mt-10">
      <button
        class="bg-pink-500 hover:bg-pink-700 text-white font-bold py-2 px-4 rounded w-24 h-10 cursor-pointer"
      >
        <p class="text-xl">Yes</p>
      </button>
      <button
        class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded w-23 h-10 cursor-pointer"
      >
        <p class="text-xl">No</p>
      </button>
    </div>
  </div>
</template>

<style scoped></style>
