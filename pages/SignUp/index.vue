<template>
  <div class="flex justify-center ml-3">
    <div class="m-20 lg:mx-20">
      <h1 class="text-primary text-5xl font-bold leading-8">Create Account</h1>
      <div>
        <form class="mt-10">
          <div class="flex justify-between">
            <div class="mb-6 flex flex-col ">
              <label 
                for="firstname" 
                class="text-primary text-xl mb-4"
              >
                First Name
              </label>
              <span class="flex flex-row justify-between items-center gap-[12px] w-[220px] h-[52px] relative">
                <input
                  type="text"
                  class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                  placeholder="John"
                />
                <img src="../../assets/person.png" alt="person" class="absolute right-3" />
              </span>
            </div>
            <div class="mb-6 flex flex-col">
              <label 
                for="lastname" 
                class="text-primary text-xl mb-4"
              >
                Last Name
              </label>
              <span class="flex flex-row justify-between items-center gap-[12px] w-[220px] h-[52px] relative">
                <input
                  type="text"
                  class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                  placeholder="Doe"
                />
                <img src="../../assets/person.png" alt="person" class="absolute right-3" />
              </span>
            </div>
          </div>

          <div class="mb-6 flex flex-col">
            <label 
              for="email" 
              class="text-primary text-xl mb-4"
            >
              Email
            </label>
            <span class="flex flex-row justify-between items-center gap-[12px] w-[464px] h-[52px] relative">
              <input
                type="email"
                class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                placeholder="johndoe@gmail.com"
              />
              <img src="../../assets/mail.png" alt="mail" class="absolute right-3" />
            </span>
          </div>

          <div class="flex justify-between">
            <div class="mb-6 flex flex-col">
              <label 
                for="password" 
                class="text-primary text-xl mb-4"
              >
                Password
              </label>
              <span class="flex flex-row justify-between items-center gap-[12px] w-[220px] h-[52px] relative">
                <input
                  type="password"
                  class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                  placeholder="*************"
                />
                <img src="../../assets/eye.png" alt="mail" class="absolute right-3" />
              </span>
            </div>
            <div class="mb-6 flex flex-col">
              <label 
                for="confirmpassword" 
                class="text-primary text-xl mb-4"
              >
                Confirm Password
              </label>
              <span class="flex flex-row justify-between items-center gap-[12px] w-[220px] h-[52px] relative">
                <input
                  type="password"
                  class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                  placeholder="**********"
                />
                <img src="../../assets/eye.png" alt="person" class="absolute right-3" />
              </span>
            </div>
          </div>
          
          <button
            class="bg-[#F0AB20] text-primary w-[464px] h-[52px] p-3 rounded-[6px] text-xl font-bold hover:bg-[#c88e1a] transition-all mt-8"
          >
            Sign In
          </button>
        </form>
        <p class="text-primary text-xl font-normal w-[464px] h-[52px] flex justify-center mt-4">
          Already a member?
          <span class="ml-2 text-[#22C1DC] hover:text-[#1b95aa] font-medium">
            <NuxtLink to="/">Sign In</NuxtLink>
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
</style>