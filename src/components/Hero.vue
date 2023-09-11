<template>
  <div
    class="flex-col justify-end items-start sm:gap-[11px] gap-1 mb-3 sm:mb-9 inline-flex"
  >
    <h2 class="text-sky-950 text-2xl sm:text-[32px] font-bold">
      {{ title.titleHeading }}
    </h2>
    <p class="text-gray-400 text-base font-normal leading-[25px]">
      {{ title.titleParagraph }}
    </p>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps(["title"]);
</script>
