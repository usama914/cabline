<template>
  <div class="container mx-auto px-4 py-10 w-3/6">
    <h1 class="text-4xl font-bold mb-6 text-center open-sans">About Nuxt Skeleton</h1>
    
    <div class="flex flex-col items-center mb-8">
      
      <div class="w-full">
        <p class="text-lg open-sans mb-4">
          The Nuxt Skeleton library is built specifically for our internal team usage. It's designed to streamline our development process and ensure consistency across projects.
        </p>
        <p class="text-lg open-sans mb-4">
          With this skeleton, we can quickly start new projects using a standardized setup. It includes our preferred technologies and configurations, saving time and reducing setup overhead.
        </p>
        <p class="text-lg open-sans mb-4">
          Our team can easily update and maintain this skeleton to reflect our evolving best practices and requirements. This ensures that all new projects benefit from our latest improvements and standards.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'About Nuxt Skeleton - Internal Development Tool',
  ogTitle: 'About Nuxt Skeleton - Internal Development Tool',
  description: 'Learn about our Nuxt Skeleton, an internal tool designed to streamline development processes and ensure consistency across projects.',
  ogDescription: 'Learn about our Nuxt Skeleton, an internal tool designed to streamline development processes and ensure consistency across projects.',
})
</script>
<style scoped>
.open-sans {
  font-family: 'Open Sans', sans-serif;
}
</style>