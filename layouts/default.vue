<template>
  <div class="flex flex-col min-h-screen">
    <HeaderComponent />
    <main class="flex flex-grow">
      <SidebarItems />
      <slot />
    </main>
  </div>
</template>

<script setup>
import HeaderComponent from "~/components/layout/HeaderComponent.vue";
import SidebarItems from "~/components/layout/SidebarItems.vue";
</script>

<style>
body {
  font-family: "Roboto", sans-serif;
  /* min-width: 710px; */
}
</style>
