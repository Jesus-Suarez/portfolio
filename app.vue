<template>

  <div class="layout">
    <Header />
    <div class="main-content"/>
    <Footer />
  </div>
</template>

<script setup>
import Footer from './components/layout/Footer.vue';
import Header from './components/layout/Header.vue';


</script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.main-content {
  flex-grow: 1;
  padding: 1rem;
  background-color: var(--color-background, #fff);
}

</style>
