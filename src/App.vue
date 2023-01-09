<script setup>
  import AppHeader from './components/AppHeader.vue';
  import AppContent from './components/AppContent.vue';
  import AppGeneralNav from './components/AppGeneralNav.vue';
</script>

<template>
  <AppHeader />
  <main>
    <AppContent />
  </main>
  <footer>
    <AppGeneralNav />
  </footer>
</template>

<style lang="scss">
  @use './style/general' as *;
</style>
