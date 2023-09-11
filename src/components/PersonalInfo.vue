<template>
  <div
    class="sm:mt-[25px] mt-[100px] p-8 rounded-[10px] shadow sm:p-0 sm:rounded-none sm:shadow-inherit"
  >
    <div class="flex-col justify-end items-start gap-[11px] mb-9 inline-flex">
      <h2 class="text-sky-950 text-[32px] font-bold">Personal info</h2>
      <p class="text-gray-400 text-base font-normal leading-[25px]">
        Please provide your name, email address, and phone number.
      </p>
    </div>

    <div class="max-w-[450px] w-full">
      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="name">Name</label>
        <input
          class="w-full pl-3 py-1 outline-none bg-white rounded-lg border-gray-300 placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="text"
          placeholder="e.g. Stephen King"
        />
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="email"
          >Email Address</label
        >
        <input
          class="w-full pl-3 py-1 outline-none bg-white rounded-lg border-gray-300 placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="email"
          placeholder="e.g. stephenking@lorem.com"
        />
      </div>

      <div
        class="flex-col justify-center items-start gap-2 inline-flex mb-4 max-w-[450px] w-full"
      >
        <label class="text-sky-950 text-sm font-normal" for="number"
          >Phone number</label
        >
        <input
          class="w-full pl-3 py-1 outline-none bg-white rounded-lg placeholder:text-gray-400 text-sky-950 text-base font-medium leading-[25px] border"
          type="number"
          placeholder="e.g. +1 234 567 890"
        />
      </div>
    </div>
  </div>
</template>
