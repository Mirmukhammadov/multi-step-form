<template>
  <div
    class="p-8 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit"
  >
    <Hero :title="title" />
    <div class="max-w-[450px] w-full">
      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="name">Name</label>
        <input
          class="w-full pl-3 py-1 outline-none focus:border focus:border-indigo-600 bg-white rounded-lg border-gray-300 placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="text"
          placeholder="e.g. Stephen King"
          v-model="state.name"
        />
        <span v-if="v$.name.$error">eror</span>
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="email"
          >Email Address</label
        >
        <input
          class="w-full pl-3 py-1 outline-none focus:border focus:border-indigo-600 bg-white rounded-lg border-gray-300 placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="email"
          placeholder="e.g. stephenking@lorem.com"
          v-model="state.email"
        />
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="number"
          >Phone number</label
        >
        <input
          class="w-full pl-3 py-1 outline-none focus:border focus:border-indigo-600 bg-white rounded-lg placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="number"
          placeholder="e.g. +1 234 567 890"
          v-model="state.number"
        />
      </div>
    </div>

    <button @childbutton="get"></button>
  </div>
</template>

<style scoped></style>

<script setup>
import Hero from "./Hero.vue";
import { ref } from "vue";
import { useVuelidate } from "@vuelidate/core";
import { required, email } from "@vuelidate/validators";
const title = {
  titleHeading: "Personal info",
  titleParagraph: "Please provide your name, email address, and phone number.",
};
const state = ref({
  name: "",
  email: "",
  number: "",
});

const rules = {
  name: { required },
  email: { required, email },
  number: { required },
};

const v$ = useVuelidate(rules, state);

function get() {
  v$.value.$validate();
  if (!v$.value.$error) {
    alert("ok");
  } else {
    alert(" not ok");
  }
}
</script>
