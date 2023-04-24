<template>
  <div class="flex">
    <Home class="w-2/4 min-h-screen" />
    
    <slot class="w-/4 h-screen" />
  </div>
</template>

<script>
  import Home from '~/components/Home.vue';
   
  export default {
    head: {
      title: 'Sapp'
    },
    components: {
      Home
    }
  }
</script>

<style scoped>

</style>