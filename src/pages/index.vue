<template>
  <div
    class="bg-[#EFF5FF] w-screen h-screen px-3 flex flex-col items-center sm:justify-center relative"
  >
    <div
      class="container sm:bg-white sm:p-5 flex flex-col justify-between sm:flex-row lg:justify-start"
    >
      <sidebar class="z-0 absolute sm:relative top-0 left-0" />
      <div
        class="flex flex-col justify-between lg:ml-[100px] sm:ml-10 sm:mt-[25px] mt-[90px]"
      >
        <PersonalInfo class="sm:z-0 back-color z-10" ref="childRef" />
        <!-- <Plan class="sm:z-0 z-10" /> -->
        <!-- <PickAddOns /> -->
        <div class="flex items-center sm:bg-inherit bg-white p-2 rounded">
          <button class="text-gray-400 text-base font-medium">Go Back</button>
          <button
            class="bg-sky-950 rounded-lg text-white text-base font-medium px-3 py-2 ml-auto mr-0"
            @click="childbutton"
          >
            Next Step
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@media screen and (max-width: 640px) {
  .container {
    max-width: 600px !important;
    width: 100%;
    justify-content: center;
    align-items: center;
  }

  .back-color {
    background-color: white;
  }
}
</style>

<script setup>
import { ref } from "vue";
import sidebar from "../components/sidebar.vue";
import PersonalInfo from "../components/PersonalInfo.vue";
import Plan from "../components/Plan.vue";
import PickAddOns from "../components/Pick-add-ons.vue";
</script>
