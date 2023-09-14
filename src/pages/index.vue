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
        <PersonalInfo class="sm:z-0 back-color z-10" v-if="pageId == 1" />
        <Plan
          class="sm:z-0 z-10"
          v-else-if="pageId == 2"
          @getLabelValue="getLabelValue"
          @buttonBoolean="buttonBoolean"
        />
        <PickAddOns
          class="sm:z-0 z-10"
          v-else-if="pageId == 3"
          @pickcheckbox="pickcheckbox"
          :planButton="planButton"
        />
        <Finishing
          class="sm:z-0 z-10"
          v-else-if="pageId == 4"
          :planLabelValue="planLabelValue"
          :pickLabelValue="pickLabelValue"
          :planButton="planButton"
        />
        <Summary v-else class="sm:z-0 z-10" />
        <div
          class="flex items-center sm:bg-inherit bg-white p-1 rounded w-full absolute bottom-0 left-0 sm:relative"
        >
          <button
            class="text-gray-400 text-base font-medium"
            @click="pageId--"
            v-if="pageId > 1 && pageId < 5"
          >
            Go Back
          </button>
          <button
            v-if="pageId < 5"
            @click="nextButton"
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
import { ref, onMounted, inject } from "vue";
import sidebar from "../components/sidebar.vue";
import PersonalInfo from "../components/PersonalInfo.vue";
import Plan from "../components/Plan.vue";
import PickAddOns from "../components/Pick-add-ons.vue";
import Finishing from "../components/Finishing.vue";
import Summary from "../components/Summary.vue";

const planButton = ref(false);
let pageId = ref(1);
let planLabelValue = ref(null);
let pickLabelValue = ref([]);
function getLabelValue(item) {
  planLabelValue.value = item;
}

function pickcheckbox(item) {
  pickLabelValue.value.push(item);
}

function nextButton() {
  if (pageId.value == 1 || pageId.value == 4) {
    pageId.value++;
  } else if (pageId.value == 2 && planLabelValue.value) {
    pageId.value++;
  } else if (pageId.value == 3 && pickLabelValue.value.length >= 1) {
    pageId.value++;
  }
}

function buttonBoolean(item) {
  planButton.value = item;
}
</script>
