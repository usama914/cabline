<template>
  <div class="container mx-auto px-4 py-10 w-3/6">
    <h1 class="text-4xl mb-6 text-center open-sans">
      Welcome to Cabline
    </h1>

    <div class="flex flex-col items-center mb-8">
      <NuxtImg
        src="/images/Nuxt-logo.png"
        class="w-64 h-auto mb-6"
        alt="Nuxt Logo"
      />

      <ButtonGroup>
        <template #primary> New </template>
      </ButtonGroup>
    </div>
  </div>
</template>

<script setup lang="ts">
import ButtonGroup from "~/components/base/ButtonGroup.vue";

useSeoMeta({
  title: "Nuxt Skeleton - Modern Web Development",
  ogTitle: "Nuxt Skeleton - Modern Web Development",
  description:
    "A powerful Nuxt-based skeleton for efficient website development with integrated PrimeVue, Tailwind CSS, and more.",
  ogDescription:
    "A powerful Nuxt-based skeleton for efficient website development with integrated PrimeVue, Tailwind CSS, and more.",
});
</script>
<style scoped>
.open-sans {
  font-family: "Open Sans", sans-serif;
}
</style>
