<template>
  <div class="mx-auto px-4 mt-10 w-full overflow-auto">
    <ManagementTable />
  </div>
</template>

<script setup lang="ts">
import ManagementTable from "../components/managementComponents/ManagementTable.vue";
</script>
<style>
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}
::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 5px;
}
</style>