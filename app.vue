<template>
  <div class="layout flex flex-col min-h-screen">
    <!-- Header -->
    <Header />

    <!-- Main Content -->
    <main class="container mx-auto flex-grow px-4">
     <section class="py-20">
      <div class="container mx-auto px-4">
        <div class="max-w-3xl mx-auto text-center">
          <h1 class="text-4xl font-bold mb-6">Full Stack Software Engineer</h1>
          <p class="text-lg text-gray-600 dark:text-gray-300 mb-8">
            Passionate about building scalable applications and solving complex problems
          </p>
          <div class="flex justify-center gap-4">
            <UButton color="primary" to="#projects">View Projects</UButton>
            <UButton color="gray" to="#contact">Contact Me</UButton>
          </div>
        </div>
      </div>
    </section>
    </main>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup lang="ts">
import Footer from './components/layout/Footer.vue';
import Header from './components/layout/Header.vue';

</script>