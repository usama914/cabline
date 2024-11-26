<template>
  <div class="w-full flex flex-col items-center gap-5">
    <h1 class="text-xl mt-5">Settings / Accounts</h1>
    <ButtonGroup @click="showModal = true">
      <template #primary> Open Model <Icon icon="prime:check" /></template>
    </ButtonGroup>
    <Model v-model:visible="showModal" header="Accounts">
      <p class="text-center">
        This is **custom content**, passed from
        <b>/managements/settings/accounts</b>.
      </p>
    </Model>
  </div>
</template>

<script setup lang="ts">
import ButtonGroup from "~/components/base/ButtonGroup.vue";
import Model from "~/components/base/Model.vue";
import { ref } from "vue";

const emit = defineEmits(["search"]);

const showModal = ref(false);
</script>
