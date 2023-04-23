<template>
  <div class="bg-primary backdrop-blur-md hidden md:flex justify-center items-center">
    <div class="flex flex-col">
      <div class="w-[377px] h-[318px] my-0 mx-auto">
        <img src="../assets/sapp.png" alt="sapp" class="w-full h-full" />
      </div>
      <div class="text-white flex flex-col">
        <h2 class="my-0 mx-auto text-[30px] font-semibold">Welcome Aboard</h2>
        <p class="font-normal mx-auto my-2">Just a couple of clicks and we start</p>
      </div>
        <div role="radiogroup" class="mx-auto my-10 gap-[8px] flex justify-center">
          <div class="flex items-center">
            <div
              class="rounded-full w-6 h-6 flex flex-shrink-0 justify-center items-center relative"
            >
              <input
                aria-labelledby="label1"
                checked
                type="radio"
                name="radio"
                class="checkbox appearance-none border rounded-full border-gray-400 absolute cursor-pointer w-full h-full checked:border-none"
              />
              <div
                class="check-icon hidden border-[9px] border-white rounded-full w-full h-full z-1"
              ></div>
            </div>
          </div>
          
          <div class="flex items-center ml-6">
            <div
              class="bg-gray-400 rounded-full w-4 h-4 flex flex-shrink-0 justify-center items-center relative"
            >
              <input
                aria-labelledby="disabled"
                disabled
                type="radio"
                name="radio"
                class="checkbox appearance-none focus:outline-none absolute cursor-pointer w-full h-full checked:border-none"
              />
              <div
                class="check-icon hidden border-4 border-indigo-700 rounded-full w-full h-full z-1"
              ></div>
            </div>
          </div>

          <div class="flex items-center ml-6">
            <div
              class="bg-gray-600 rounded-full w-4 h-4 flex flex-shrink-0 justify-center items-center relative"
            >
              <input
                aria-labelledby="disabled"
                disabled
                type="radio"
                name="radio"
                class="checkbox appearance-none focus:outline-none absolute cursor-pointer w-full h-full checked:border-none"
              />
              <div
                class="check-icon hidden border-4 border-indigo-700 rounded-full w-full h-full z-1"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<style scoped>
.checkbox:checked {
  border: none;
}
.checkbox:checked + .check-icon {
  display: flex;
}
</style>