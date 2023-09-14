<template>
  <div
    class="mobile_img back_img w-screen h-[170px] sm:rounded sm:max-w-[275px] sm:w-full sm:max-h-[570px] sm:h-screen"
  >
    <div class="flex justify-center items-center sm:flex-col sm:items-start">
      <div v-for="item in sidebarValue" :key="item">
        <div class="mt-8 px-7 flex">
          <span
            class="w-[33px] h-[33px] text-center py-1.5 text-white text-sm font-bold uppercase tracking-wide rounded-full border border-white duration-300"
            :class="{
              'bg-sky-200': item.id == id,
              'text-[black]': item.id == id,
            }"
            >{{ item.id }}</span
          >
          <div class="ml-4 sm:block hidden">
            <p class="text-indigo-300 text-xs font-normal">{{ item.step }}</p>
            <h1 class="text-white text-sm font-bold uppercase tracking-wide">
              {{ item.info }}
            </h1>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.back_img {
  display: block;
  background-repeat: no-repeat;
  background-image: url("../assets/images/bg-sidebar-desktop.svg");
  background-size: cover;
  background-position: center center;
}

@media only screen and (max-width: 640px) {
  .mobile_img {
    background-image: url("../assets/images/bg-sidebar-mobile.svg");
    display: block;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;
  }
}
</style>

<script setup>
import { ref, defineProps } from "vue";
const props = defineProps(["id"]);
const sidebarValue = [
  {
    id: 1,
    step: "step 1",
    info: "YOUR INFO",
  },
  {
    id: 2,
    step: "step 2",
    info: "SELECT PLAN",
  },
  {
    id: 3,
    step: "step 3",
    info: "ADD-ONS",
  },
  {
    id: 4,
    step: "step 4",
    info: "SUMMARY",
  },
];
</script>
