<template>
  <div
    class="flex flex-col sm:bg-inherit bg-white p-5 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit"
  >
    <hero :title="title" />
    <div v-for="item in pickValues" :key="item.id" class="mb-5">
      <input
        type="checkbox"
        :id="item.id"
        class="hidden"
        v-model="item.boolean.value"
      />
      <label
        :for="item.id"
        class="max-w-[450px] w-full h-20 p-5 flex rounded-lg border cursor-pointer"
        :class="{ label: item.boolean.value }"
        @click="$emit('pickcheckbox', item)"
      >
        <span
          class="w-5 h-5 bg-[#483EEF] rounded flex justify-center items-center mt-2 border border-gray"
          :class="{ 'bg-[#fff]': !item.boolean.value }"
        >
          <img
            src="../assets/images/icon-checkmark.svg"
            v-if="item.boolean.value"
            alt=""
            class=""
          />
        </span>
        <div class="flex flex-col justify-center ml-4">
          <p class="text-sky-950 text-base font-medium">{{ item.name }}</p>
          <p class="text-gray-400 text-sm font-normal leading-tight">
            {{ item.paragraph }}
          </p>
        </div>
        <span
          v-if="!props.planButton"
          class="text-right text-indigo-600 text-sm font-normal leading-tight ml-auto mr-3 mt-2"
          >+${{ item.price }}/mo</span
        >
        <span
          v-if="props.planButton"
          class="text-right text-indigo-600 text-sm font-normal leading-tight ml-auto mr-3 mt-2"
          >+${{ item.yearlyPrice }}/yr</span
        >
      </label>
    </div>
  </div>
</template>

<style scooped>
.label {
  background: #f8f9ff;
  border-radius: 8px;
  border: 0.5px #483eff solid;
}
</style>

<script setup>
import { ref, defineProps } from "vue";
import hero from "./Hero.vue";
const title = {
  titleHeading: "Pick add-ons",
  titleParagraph: "Add-ons help enhance your gaming experience.",
};

const props = defineProps(["planButton"]);
const pickValues = [
  {
    id: "option1",
    name: "Online service",
    paragraph: "Access to multiplayer games",
    price: 1,
    yearlyPrice: 10,
    boolean: ref(false),
  },
  {
    id: "option2",
    name: "Larger storage",
    paragraph: "Extra 1TB of cloud save",
    price: 2,
    yearlyPrice: 20,
    boolean: ref(false),
  },
  {
    id: "option3",
    name: "Customizable profile",
    paragraph: "Custom theme on your profile",
    price: 2,
    yearlyPrice: 20,
    boolean: ref(false),
  },
];
</script>
