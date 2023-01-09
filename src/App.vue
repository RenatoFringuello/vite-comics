<script setup>
  import AppHeader from './components/AppHeader.vue';
  import AppContent from './components/AppContent.vue';
  import AppMainNav from './components/AppMainNav.vue';
</script>

<template>
  <AppHeader />
  <main>
    <AppContent />
    <AppMainNav />
  </main>
</template>

<style lang="scss">
  @use './style/general' as *;
</style>
