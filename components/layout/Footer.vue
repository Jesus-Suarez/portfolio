<template>
	<div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <p>&copy; 2024 Jesús Suárez Álvarez. All rights reserved.</p>
          <div class="flex gap-4 mt-4 md:mt-0">
            <UButton
              v-for="social in socials"
              :key="social.name"
              :to="social.url"
              target="_blank"
              variant="ghost"
              color="gray"
            >
              {{ social.name }}
            </UButton>
          </div>
        </div>
      </div>
</template>

<script setup lang="ts">
const socials = [
  { name: 'GitHub', url: 'https://github.com/Jesus-Suarez' },
  { name: 'LinkedIn', url: 'https://www.linkedin.com/in/jesus-suarz/' },
];

</script>