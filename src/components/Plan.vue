<style>
.square-radio:checked + label {
  background: #f8f9ff;
  border-radius: 8px;
  border: 0.5px #483eff solid;
}
</style>

<template>
  <div class="flex flex-col ml-20">
    <div class="mt-10 flex justify-center">
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
            class="w-[138px] h-40 bg-white rounded-lg border border-gray-300 ml-4 p-4 flex flex-col justify-between"
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
      class="ml-4 mt-8 w-[96%] h-12 bg-slate-50 rounded-lg flex justify-center items-center"
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

<script setup>
import { ref } from "vue";
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
