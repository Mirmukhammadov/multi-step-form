<template>
  <div
    class="flex flex-col bg-white sm:bg-inherit p-5 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit"
  >
    <hero :title="title" />
    <div class="flex flex-col justify-center sm:flex-row flex-wrap">
      <div v-for="item in Plan" :key="item.id">
        <div>
          <input
            type="radio"
            class="square-radio hidden"
            :id="item.id"
            name="options"
          />
          <label
            :for="item.id"
            class="w-[90%] h-auto bg-white rounded-lg border border-gray-300 p-4 flex flex-row gap-5 my-2 items-center sm:m-1 sm:gap-3 sm:h-40 sm:w-[138px] sm:flex-col sm:justify-between sm:items-start"
          >
            <img
              src="../assets/images/icon-arcade.svg"
              alt=""
              class="w-10 h-10 mb-2"
            />
            <div class="text-left">
              <p class="text-sky-950 text-base font-medium">{{ item.name }}</p>
              <span class="text-gray-400 text-sm font-normal">{{
                item.price
              }}</span>
              <p class="text-sky-950 text-xs font-normal" v-if="buttonBoolean">
                {{ item.yearlyPrice }}
              </p>
            </div>
          </label>
        </div>
      </div>
    </div>

    <div
      class="mt-4 sm:mt-8 w-[90%] sm:w-full h-12 bg-slate-50 rounded-lg flex justify-center items-center"
    >
      <p
        class="text-right text-gray-400 text-sm font-medium"
        :class="{ 'text-sky-950': !buttonBoolean }"
      >
        Monthly
      </p>
      <button class="px-6" @click="buttonBoolean = !buttonBoolean">
        <img src="../assets/images/left.png" alt="" v-if="!buttonBoolean" />
        <img src="../assets/images/right.png" alt="" v-else />
      </button>
      <p
        class="text-right text-gray-400 text-sm font-medium"
        :class="{ 'text-sky-950': buttonBoolean }"
      >
        Yearly
      </p>
    </div>
  </div>
</template>

<style>
.square-radio:checked + label {
  background: #f8f9ff;
  border-radius: 8px;
  border: 0.5px #483eff solid;
}

label:hover {
  border: 0.5px #483eff solid;
}

/* @media only screen and (max-width: 680px) {
  .div {
    flex-wrap: nowrap !important;
  }
} */
</style>

<script setup>
import { ref } from "vue";
import hero from "./Hero.vue";
const title = {
  titleHeading: "Select your plan",
  titleParagraph: "You have the option of monthly or yearly billing.",
};
const buttonBoolean = ref(true);
const Plan = [
  {
    id: "option1",
    img: "../assets/images/icon-arcade.svg",
    name: "Arcade",
    price: "$9/mo",
    yearlyPrice: " 2 months free",
  },
  {
    id: "option2",
    img: "../assets/images/icon-advanced.svg",
    name: "Advanced",
    price: "$12/mo",
    yearlyPrice: " 2 months free",
  },
  {
    id: "option3",
    img: "../assets/images/icon-pro.svg",
    name: "Pro",
    price: "$15/mo",
    yearlyPrice: " 2 months free",
  },
];
</script>
