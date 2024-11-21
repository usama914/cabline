<template>
  <div class="mx-auto px-4 mt-10 w-100 lg:w-4/5" >
    <ManagementHeader></ManagementHeader>
    <ManagementTable />
    <!-- <SidebarItems/> -->
  </div>
</template>

<script setup lang="ts">
import ManagementHeader from "~/components/managementComponents/ManagementHeader.vue";
import ManagementTable from "../components/managementComponents/ManagementTable.vue";
// import SidebarItems from "~/components/SidebarItems.vue";

useSeoMeta({
  title: "About Nuxt Skeleton - Internal Development Tool",
  ogTitle: "About Nuxt Skeleton - Internal Development Tool",
  description:
    "Learn about our Nuxt Skeleton, an internal tool designed to streamline development processes and ensure consistency across projects.",
  ogDescription:
    "Learn about our Nuxt Skeleton, an internal tool designed to streamline development processes and ensure consistency across projects.",
});
</script>
<style scoped>
.open-sans {
  font-family: "Open Sans", sans-serif;
}
</style>
