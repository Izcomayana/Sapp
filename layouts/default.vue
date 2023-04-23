<template>
  <div class="flex">
    <Home class="w-2/4 h-screen" />
    
    <slot class="w-/4 h-screen" />
  </div>
</template>

<script>
  import Home from '~/components/Home.vue';
   
  export default {
    components: {
      Home
    }
  }
</script>

<style scoped>

</style>