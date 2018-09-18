<template>
  <div class="container__contacts">
    <AppEmail/>
  </div>
</template>

<script>
  import AppEmail from '@/components/AppEmail.vue';

  export default {
    name: 'contacts',
    components: {
      AppEmail
    }
  }
</script>

<style scoped>
  .container__contacts {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
  }
</style>
