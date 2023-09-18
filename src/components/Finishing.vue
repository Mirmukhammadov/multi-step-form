<template>
  <div
    class="flex flex-col bg-white sm:bg-inherit p-5 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit"
  >
    <Hero :title="title" />
    <div class="max-w-[450px] w-full">
      <div class="bg-slate-50 rounded-lg py-5 px-6">
        <div class="flex justify-between items-center mb-5">
          <div>
            <p class="text-sky-950 text-base font-medium font-['Ubuntu']">
              {{ props.planLabelValue.name }}
            </p>
            <button
              class="text-gray-400 text-sm font-normal font-['Ubuntu'] underline leading-tight"
            >
              change
            </button>
          </div>
          <p
            v-if="!props.planButton"
            class="text-right text-sky-950 text-base font-bold font-['Ubuntu'] leading-tight"
          >
            ${{ props.planLabelValue.price }}/mo
          </p>

          <p
            v-if="props.planButton"
            class="text-right text-sky-950 text-base font-bold font-['Ubuntu'] leading-tight"
          >
            ${{ props.planLabelValue.yearlyPrice }}/yr
          </p>
        </div>
        <span class="block w-full h-px opacity-20 bg-gray-400 mb-5"></span>
        <div
          class="flex justify-between mb-5"
          v-for="obj in props.pickLabelValue"
          :key="obj"
        >
          <p
            class="text-gray-400 text-sm font-normal font-['Ubuntu'] leading-tight"
          >
            {{ obj.name }}
          </p>
          <p
            v-if="!props.planButton"
            class="text-right text-sky-950 text-sm font-normal font-['Ubuntu'] leading-tight"
          >
            +${{ obj.price }}/mo
          </p>
          <p
            v-if="props.planButton"
            class="text-right text-sky-950 text-sm font-normal font-['Ubuntu'] leading-tight"
          >
            +${{ obj.yearlyPrice }}/yr
          </p>
        </div>
      </div>
      <div class="flex justify-between py-5 px-6">
        <p
          class="text-gray-400 text-sm font-normal font-['Ubuntu'] leading-tight"
        >
          Total
        </p>
        <p
          v-if="!props.planButton"
          class="text-right text-indigo-600 text-xl font-bold font-['Ubuntu'] leading-tight"
        >
          ${{ getTotal }}/mo
        </p>

        <p
          v-if="props.planButton"
          class="text-right text-indigo-600 text-xl font-bold font-['Ubuntu'] leading-tight"
        >
          ${{ getTotal }}/yr
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

import Hero from "./Hero.vue";
let getTotal = ref(0);
const title = {
  titleHeading: "Finishing up",
  titleParagraph: "Double-check everything looks OK before confirming.",
};

const props = defineProps(["planLabelValue", "pickLabelValue", "planButton"]);
const price = ref(0);
const numericValue = ref();
if (!props.planButton) {
  getTotal.value = props.planLabelValue.price;

  for (const i in props.pickLabelValue) {
    getTotal.value += props.pickLabelValue[i].price;
  }
}

if (props.planButton) {
  getTotal.value = props.planLabelValue.yearlyPrice;

  for (const i in props.pickLabelValue) {
    getTotal.value += props.pickLabelValue[i].yearlyPrice;
  }
}
</script>

<style scoped></style>
