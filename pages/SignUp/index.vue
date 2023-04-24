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

          <div class="flex flex-col justify-between">
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
                    :type="isPasswordVisible ? 'text' : 'password'" 
                    v-model="password"
                    class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                    placeholder="*************"
                  />
                  <button 
                    type="button" 
                    class="absolute right-3" 
                    @click="togglePasswordVisibility" 
                  >
                    <img v-if="!isPasswordVisible" src="../../assets/eye.png" alt="show"/>
                    <img v-else src="../../assets/eye.svg" alt="hide">
                </button>
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
                    :type="isPasswordVisible ? 'text' : 'password'" 
                    v-model="confirmPassword"
                    class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                    placeholder="**********"
                  />
                  <button 
                    type="button" 
                    class="absolute right-3" 
                    @click="togglePasswordVisibility" 
                  >
                    <img v-if="!isPasswordVisible" src="../../assets/eye.png" alt="show"/>
                    <img v-else src="../../assets/eye.svg" alt="hide">
                  </button>
                </span>
              </div>
            </div>
            <div class="flex flex-col">
              <div>
                <div v-for="(criterion, index) in criteria" :key="index">
                  <input type="radio"
                    :name="criterion.name"
                    :value="'yes'"
                    :checked="criterion.isChecked === 'yes'"
                    class="mr-2 appearance-none border rounded-full border-gray-400 w-3.5 h-3.5 checked:border-none checked:bg-[#22C1DC]"
                    disabled
                  /> 
                  <span 
                    :class="criterion.isChecked === 'yes' ? 'text-[#22C1DC]' : 'text-primary'"
                  >
                      {{ criterion.label }}
                  </span>
                  <br />
                </div>
              </div>
            </div>
          </div>
          
          <button
            type="submit"
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

<script>
import { ref, watch } from "vue"

export default {
  setup() {
    const password = ref('');
    const confirmPassword = ref('');
    const isPasswordVisible = ref(false);
    const criteria = ref([
      { label: 'At least 8 characters', name: 'length', isChecked: 'no' },
      { label: 'Contains uppercase letters', name: 'uppercase', isChecked: 'no' },
      { label: 'Contains lowercase letters', name: 'lowercase', isChecked: 'no' },
      { label: 'Contains numbers', name: 'numbers', isChecked: 'no' },
    ]);

    function togglePasswordVisibility() {
      isPasswordVisible.value = !isPasswordVisible.value;
    }

    watch(password, (newValue) => {
      let count = 0;

      if (newValue.length >= 8) {
        criteria.value[0].isChecked = 'yes';
        count++;
      } else {
        criteria.value[0].isChecked = 'no';
      }

      if (/[A-Z]/.test(newValue)) {
        criteria.value[1].isChecked = 'yes';
        count++;
      } else {
        criteria.value[1].isChecked = 'no';
      }

      if (/[a-z]/.test(newValue)) {
        criteria.value[2].isChecked = 'yes';
        count++;
      } else {
        criteria.value[2].isChecked = 'no';
      }

      if (/\d/.test(newValue)) {
        criteria.value[3].isChecked = 'yes';
        count++;
      } else {
        criteria.value[3].isChecked = 'no';
      }
    });

    return {
      password,
      confirmPassword,
      isPasswordVisible,
      togglePasswordVisibility,
      criteria,
    };
  }
}
</script>

<style scoped>
</style>