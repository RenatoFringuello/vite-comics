<script setup>
  import AppHeader from './components/AppHeader.vue';
  import AppContent from './components/AppContent.vue';
  import AppGeneralNav from './components/AppGeneralNav.vue';
  import AppAllNav from './components/AppAllNav.vue';
  import AppSignUp from './components/AppSignUp.vue';
</script>

<template>
  <AppHeader />
  <main>
    <AppContent />
  </main>
  <footer>
    <AppGeneralNav />
    <AppAllNav />
    <AppSignUp />
  </footer>
</template>

<style lang="scss">
  @use './style/general' as *;
</style>
