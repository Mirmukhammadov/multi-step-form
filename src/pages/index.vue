<template>
  <div
    class="bg-[#EFF5FF] w-screen h-screen px-3 flex flex-col items-center sm:justify-center relative"
  >
    <div
      class="container sm:bg-white sm:p-5 flex flex-col sm:flex-row sm:justify-start"
    >
      <sidebar
        class="z-0 absolute sm:relative sm:mt-5 md:mt-0 top-0 left-0"
        :id="pageId"
      />
      <div
        class="flex flex-col justify-between sm:ml-10 sm:mt-[25px] mt-[90px]"
      >
        <PersonalInfo
          class="sm:z-0 back-color z-10 lg:ml-[100px] md:ml-[50px]"
          v-if="pageId == 1"
        />
        <Plan class="sm:z-0 z-10" v-else-if="pageId == 2" />
        <PickAddOns class="sm:z-0 z-10" v-else-if="pageId == 3" />
        <div
          class="flex items-center sm:bg-inherit bg-white p-1 rounded w-full absolute bottom-0 left-0 sm:relative"
        >
          <button
            class="text-gray-400 text-base font-medium"
            @click="pageId--"
            v-if="pageId > 1"
          >
            Go Back
          </button>
          <button
            @click="pageId++"
            class="bg-sky-950 rounded-lg text-white text-base font-medium px-3 py-2 ml-auto mr-0"
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

const toggle = ref(false);

const pageId = ref(1);
</script>
