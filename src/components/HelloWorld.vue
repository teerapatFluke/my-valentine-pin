<script setup lang="ts">
import { ref } from "vue";

const status = ref(false);
const yesImg = ref(new URL("@/assets/together.jpg", import.meta.url).href);
const beautyImg = ref(new URL("@/assets/beauty.jpg", import.meta.url).href);
const sadArray = ref([
  new URL("@/assets/sad0.gif", import.meta.url).href,
  new URL("@/assets/sad1.gif", import.meta.url).href,
  new URL("@/assets/sad2.gif", import.meta.url).href,
  new URL("@/assets/sad3.gif", import.meta.url).href,
  new URL("@/assets/sad4.gif", import.meta.url).href,
  new URL("@/assets/sad5.gif", import.meta.url).href,
  new URL("@/assets/sad6.webp", import.meta.url).href,
  new URL("@/assets/sad7.gif", import.meta.url).href,
  new URL("@/assets/sad8.gif", import.meta.url).href,
  new URL("@/assets/upset.jpg", import.meta.url).href,
]);
const currentSad = ref(beautyImg);
const bg = ref([
  "bg-pink-200",
  "bg-pink-300",
  "bg-pink-400",
  "bg-pink-500",
  "bg-pink-600",
  "bg-pink-700",
  "bg-pink-800",
  "bg-pink-900",
  "bg-black",
  `bg-[url('https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/c58a6b24-9998-464f-87da-1c45d1b89a4c/dbuynxy-5a815bfd-d64e-4dba-bc28-d0d819ab056d.gif?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2M1OGE2YjI0LTk5OTgtNDY0Zi04N2RhLTFjNDVkMWI4OWE0Y1wvZGJ1eW54eS01YTgxNWJmZC1kNjRlLTRkYmEtYmMyOC1kMGQ4MTlhYjA1NmQuZ2lmIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.EBsLNN8FJquNYrkkUikb5CAuDFdCkftBOTmgjrJSzLc')] bg-cover bg-center`,
]);

const noText = ref([
  "Please reconsider",
  "Give it another thought",
  "Just one more chance",
  "I beg you, think again.",
  "Please don’t decide just yet",
  "Can you rethink this?",
  "Please, have a second thought",
  "I’m asking you, please reconsider",
  "Please, don’t say no",
  "I’m begging you, please reconsider",
]);
const currentText = ref("Will you be my valentine ?");
const curentBg = ref("bg-pink-200");
const sadIndex = ref(0);

const voteNo = () => {
  status.value = false;
  if (sadIndex.value < sadArray.value.length - 1) {
    sadIndex.value = sadIndex.value + 1;
    curentBg.value = bg.value[sadIndex.value];
    currentText.value = noText.value[sadIndex.value];
    currentSad.value = sadArray.value[sadIndex.value];
    console.log(sadIndex.value);
  }
};

const voteYes = () => {
  sadIndex.value = 0;
  curentBg.value = `bg-[url('https://i.pinimg.com/originals/ee/c1/24/eec1243b10dbb3cb10679d68f0681a33.gif')] bg-cover bg-center`;
  console.log(curentBg.value);
  currentSad.value = yesImg.value;
  status.value = true;
};
</script>

<template>
  <div :class="`w-full grid grid-cols-12 h-screen ${curentBg}`">
    <div
      class="col-span-3 p-4 rounded flex flex-col justify-center items-center"
    >
      <img v-if="status" src="@/assets/valentine.png" alt="heart" />
      <img v-if="status" src="@/assets/love.png" alt="heart" />
    </div>
    <div class="col-span-6">
      <p class="text-center text-6xl text-white">{{ currentText }}</p>
      <div
        class="mx-auto w-64 h-64 border-2 border-black overflow-hidden mt-10"
      >
        <img
          :src="currentSad"
          alt="example"
          class="w-full h-full object-cover object-center"
        />
      </div>

      <div class="flex justify-center gap-4 mt-10">
        <button
          @click="voteYes"
          class="bg-pink-500 border-1 hover:bg-pink-700 text-white font-bold py-2 px-4 rounded w-24 h-10 cursor-pointer"
        >
          <p class="text-xl">Yes</p>
        </button>
        <button
          v-if="sadIndex < sadArray.length - 1"
          @click="voteNo"
          class="bg-red-500 border-1 hover:bg-red-700 text-white font-bold py-2 px-4 rounded w-23 h-10 cursor-pointer"
        >
          <p class="text-xl">No</p>
        </button>
      </div>
      <div
        class="mx-auto w-100 h-50 border-2 border-black overflow-hidden mt-10"
        v-if="status"
      >
        <iframe
          class="w-full h-full object-cover object-center"
          src="https://www.youtube.com/embed/OYPiXBIgvJ8?start=69"
          title="เพลงรัก - Three Man Down |Official MV|"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          referrerpolicy="strict-origin-when-cross-origin"
          allowfullscreen
        ></iframe>
      </div>
    </div>
    <div
      v-if="status"
      class="col-span-3 flex flex-col justify-center items-center"
    >
      <p class="text-white text-center text-4xl">
        Happy Valentine's Day, my love. Even though we are not together this
        year, my love for you remains constant. I wish you lots of happiness.
        Let's spend every Valentine's Day together from now on. Happy
        Valentine's Day!
      </p>
      <img
        class="max-w-full h-64 mt-4 border"
        src="@/assets/IMG_7245.jpg"
        alt="heart"
      />
    </div>
  </div>
</template>

<style scoped></style>
