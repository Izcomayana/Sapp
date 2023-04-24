<template>
  <div class="flex justify-center ml-3">
    <div class="m-20 lg:mx-20">
      <h1 class="text-primary text-5xl font-bold leading-8">Create Account</h1>
      <div>
        <form class="mt-10" @submit.prevent="submitForm">
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
                  v-model="firstName"
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
                  v-model="lastName"
                  class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                  placeholder="Doe"
                  required
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
                v-model="email"
                class="rounded-[6px] text-primary bg-[#F4F2F2] w-full h-full absolute p-3 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary"
                placeholder="johndoe@gmail.com"
                required
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
                    required
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
                    required
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
                  <input 
                    type="radio"
                    :id="criterion.name"
                    :name="criterion.name"
                    :value="'yes'"
                    :checked="criterion.isChecked === 'yes'"
                    class="mr-2 appearance-none border rounded-full border-gray-400 w-3.5 h-3.5 checked:border-none checked:bg-[#22C1DC]"
                    @change="updateCriterion(index, $event.target.checked)"
                    disabled
                  /> 
                  <label 
                    :for="criterion.name"
                    :class="criterion.isChecked === 'yes' ? 'text-[#22C1DC]' : 'text-primary'"
                  >
                    {{ criterion.label }}
                  </label>
                  <span :class="criterion.isChecked === 'yes' ? 'hidden' : 'required'">*</span>
                </div>
              </div>
            </div>
          </div>
          
          <button
            type="submit"
            class="bg-[#F0AB20] text-primary w-[464px] h-[52px] p-3 rounded-[6px] text-xl font-bold hover:bg-[#c88e1a] transition-all mt-8 disabled:opacity-25"
            @click="submitForm"
            :disabled="!firstName || !lastName || !email || !password || !confirmPassword || hasRequiredFields"
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
import { ref, watch, computed } from "vue"

export default {
  setup() {
    const firstName = ref('John');
    const lastName = ref('Emanuela');
    const email = ref('johndoe@gmail.com');
    const password = ref('Mayana12');
    const confirmPassword = ref('Mayana12');
    const isPasswordVisible = ref(false);
    const criteria = ref([
      { label: 'At least 8 characters', name: 'length', isChecked: 'no', required: true },
      { label: 'Contains at least one uppercase letter', name: 'uppercase', isChecked: 'no', required: true },
      { label: 'Contains lowercase letters', name: 'lowercase', isChecked: 'no', required: true },
      { label: 'Contains numbers', name: 'numbers', isChecked: 'no', required: true },
    ]);

    const togglePasswordVisibility = () => {
      isPasswordVisible.value = !isPasswordVisible.value;
    }

    const isEmailValid = (email) => {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    }

    const hasRequiredFields = computed(() => {
      return criteria.value.some((criterion) => criterion.required && criterion.isChecked === 'no');
    });

    function updateCriterion(index, checked) {
      criteria.value[index].isChecked = checked ? 'yes' : 'no';
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

    const submitForm = () => {
      if(confirmPassword.value !== password.value) {
        alert('confirm password is different from password')
      } else if (isEmailValid(email.value)) {
        // email is valid, submit the form
        alert('Form submitted!');
        firstName.value = ""
        lastName.value = ""
        email.value = ""
        password.value = ""
        confirmPassword.value = ""
      } else {
        alert('invalid email')
      }
    };

    return {
      firstName,
      lastName,
      email,
      password,
      confirmPassword,
      isPasswordVisible,
      isEmailValid,
      togglePasswordVisibility,
      criteria,
      hasRequiredFields,
      updateCriterion,
      submitForm,
    };
  }
}
</script>

<style scoped>
  .error {
    color: red;
  }
  .required {
    color: red;
    font-weight: bold;
  }
</style>