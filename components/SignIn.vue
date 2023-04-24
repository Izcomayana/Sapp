<template>
  <div class="flex justify-center ml-3">
    <div class="m-20 lg:mt-28 lg:mx-20">
      <h1 class="text-primary text-5xl font-bold leading-8">Sign In</h1>
      <div>
        <form class="mt-10" @submit.prevent="submitForm">
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
                v-model="email"
                class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                placeholder="johndoe@gmail.com"
                required
              />
              <img src="../assets/mail.png" alt="mail" class="absolute right-3" />
            </span>
          </div>

          <div class="mb-6 flex flex-col">
            <label 
              for="email" 
              class="text-primary text-xl mb-4"
            >
              Password
            </label>
            <span class="flex flex-row justify-between items-center gap-[12px] w-[464px] h-[52px] relative">
              <input
                :type="isPasswordVisible ? 'text' : 'password'" 
                v-model="password"
                class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                placeholder="*************"
                required
              />
              <button 
                type="button" 
                class="absolute right-3" 
                @click="togglePasswordVisibility" 
              >
                <img v-if="!isPasswordVisible" src="../assets/eye.png" alt="show"/>
                <img v-else src="../assets/eye.svg" alt="hide">
              </button>
            </span>
          </div>
          <button 
            type="submit"
            class="bg-[#F0AB20] text-primary w-[464px] h-[52px] p-3 rounded-[6px] text-xl font-bold hover:bg-[#c88e1a] transition-all mt-8 disabled:opacity-25"
            data-te-toggle="modal"
            data-te-target="#exampleModalCenter"
            data-te-ripple-init
            data-te-ripple-color="light"
            @click="submitForm"
            :disabled="!email || !password"
            >
            Sign In
          </button>
        </form>
        <p class="text-primary text-xl font-normal w-[464px] h-[52px] flex justify-center mt-4">
          Don’t have an account?
          <span class="ml-2 text-[#22C1DC] hover:text-[#1b95aa] font-medium">
            <NuxtLink to="/signup">Sign Up</NuxtLink>
          </span>
        </p>
      </div>

      <div v-if="showModal" @click="showModal = false">
        <div class="fixed z-10 inset-0 overflow-y-auto">
          <div class="flex items-center justify-center min-h-screen">
            <div class="fixed inset-0 bg-gray-500 bg-opacity-75"></div>
            <div class="bg-white rounded-lg overflow-hidden shadow-xl transform transition-all sm:w-full sm:max-w-lg">
              <div class="px-6 py-4">
                <div class="flex items-center justify-between">
                </div>
                <p class="mt-4">
                  Log In Successfully ✔
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue"

export default {
  setup() {
    const email = ref('');
    const password = ref('');
    const isPasswordVisible = ref(false);
    const showModal = ref(false)

    function togglePasswordVisibility() {
      isPasswordVisible.value = !isPasswordVisible.value;
    }

    const isEmailValid = (email) => {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    }

    const submitForm = () => {
      if (isEmailValid(email.value)) {
        email.value = ""
        password.value = ""
        showModal.value = true;
      } else {
        alert('invalid email')
      }
    };

    return {
      email,
      password,
      isPasswordVisible,
      showModal,
      togglePasswordVisibility,
      isEmailValid,
      submitForm
    };
  }
}
</script>

<style scoped>
</style>