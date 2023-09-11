<template>
  <div class="flex flex-col">
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
        class="w-[450px] h-20 p-5 flex rounded-lg border"
        :class="{ label: item.boolean.value }"
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
          class="text-right text-indigo-600 text-sm font-normal leading-tight ml-auto mr-3 mt-2"
          >{{ item.price }}</span
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
import { ref } from "vue";
import hero from "./Hero.vue";
const title = {
  titleHeading: "Pick add-ons",
  titleParagraph: "Add-ons help enhance your gaming experience.",
};
const pickValues = [
  {
    id: "option1",
    name: "Online service",
    paragraph: "Access to multiplayer games",
    price: "+$1/mo",
    boolean: ref(false),
  },
  {
    id: "option2",
    name: "Larger storage",
    paragraph: "Extra 1TB of cloud save",
    price: "+$2/mo",
    boolean: ref(false),
  },
  {
    id: "option3",
    name: "Customizable profile",
    paragraph: "Custom theme on your profile",
    price: "+$2/mo",
    boolean: ref(false),
  },
];
</script>
