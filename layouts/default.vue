<template>
  <div class="flex flex-col min-h-screen">
    <HeaderComponent />
    <main class="flex flex-grow">
      <SidebarItems></SidebarItems>
      <slot />
    </main>
  </div>
</template>

<script setup lang="ts">
import HeaderComponent from "~/components/HeaderComponent.vue";
import SidebarItems from "~/components/SidebarItems.vue";
</script>

<style>
body {
  font-family: "Roboto", sans-serif;
}

.open-sans {
  font-family: "Open Sans", sans-serif;
}
</style>
