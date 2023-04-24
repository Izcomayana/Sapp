<template>
  <div>
    <SignIn />
  </div>
</template>

<script>
import SignIn from '~/components/SignIn.vue';
  export default {
    components: {
      SignIn
    }
  }
</script>

<style scoped>
.page-enter-active,
.page-leave-active {
  transition: all 0.5s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>