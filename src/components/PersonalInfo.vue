<template>
  <div
    class="p-8 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit max-w-[400px] w-full"
  >
    <Hero :title="title" />
    <div class="max-w-[450px] w-full">
      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="name">Name</label>
        <input
          class="input"
          :class="{ error: v$.name.$error }"
          type="text"
          required
          placeholder="e.g. Stephen King"
          v-model="state.name"
        />
        <span
          v-if="v$.name.$error"
          class="text-right text-red-500 text-sm font-bold"
          >This field is required</span
        >
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="email"
          >Email Address</label
        >
        <input
          class="input"
          required
          :class="{ error: v$.email.$error }"
          type="email"
          placeholder="e.g. stephenking@lorem.com"
          v-model="state.email"
        />
        <span
          v-if="v$.email.$error"
          class="text-right text-red-500 text-sm font-bold"
          >This field is required</span
        >
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="number"
          >Phone number</label
        >
        <input
          class="input"
          required
          :class="{ error: v$.number.$error }"
          type="number"
          placeholder="e.g. +1 234 567 890"
          v-model="state.number"
        />
        <span
          v-if="v$.number.$error"
          class="text-right text-red-500 text-sm font-bold"
          >This field is required</span
        >
      </div>
    </div>
  </div>
</template>

<style scoped>
.input {
  width: 100%;
  padding-left: 0.75rem;
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
  outline: none;
  border: 1px solid #d1d5db;
  background-color: #ffffff;
  border-radius: 0.375rem;
  border-color: #d1d5db;
  color: #1e3a8a;
  font-size: 1rem;
  font-weight: 500;
  line-height: 25px;
}

.input::placeholder {
  color: #9ca3af;
}

.input:focus {
  border: 0.5px #483eff solid;
}

.error {
  border-color: red;
}
</style>

<script setup>
import Hero from "./Hero.vue";
import { ref, defineEmits } from "vue";
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
const formErrors = ref();
const rules = {
  name: { required },
  email: { required, email },
  number: { required },
};

const v$ = useVuelidate(rules, state);

function get() {
  v$.value.$validate();
  formErrors.value = v$.value.$errors;
}
</script>
