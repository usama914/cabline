<template>
  <div class="mx-auto px-4 mt-10 w-100 lg:w-4/5 overflow-auto">
    <ManagementHeader />
    <ManagementTable />
  </div>
</template>

<script setup lang="ts">
import ManagementHeader from "~/components/managementComponents/ManagementHeader.vue";
import ManagementTable from "../components/managementComponents/ManagementTable.vue";
</script>
<style scoped>
</style>
