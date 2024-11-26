<template>
  <div
    class="h-100 w-60 flex-col items-center p-4 hidden lg:flex"
    :style="{ backgroundColor: 'var(--color-neutral-semilight)' }"
  >
    <div class="w-48">
      <div class="title mb-4">
        <h1 class="font-mitr text-base uppercase tracking-widest">
          {{ title }}
        </h1>
      </div>
      <div class="card flex justify-center">
        <PanelMenu
          multiple
          :model="items"
          class="w-full md:w-80 !text-red"
          style="
            --p-panelmenu-panel-background: var(
              --color-neutral-semilight
            ) !important;
          "
        >
          <template #item="{ item }">
            <NuxtLink
              :to="item.route"
              class="flex items-center cursor-pointer text-surface-700 dark:text-surface-0 px-4 py-2"
            >
              <Icon :icon="item.icon" class="text-lg" />
              <span class="ml-2">{{ item.label }}</span>
              <Icon
                v-if="item.items"
                class="ml-auto"
                icon="mdi:arrow-down-drop"
              />
            </NuxtLink>
          </template>
        </PanelMenu>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

interface MenuItem {
  label: string;
  icon?: string;
  route?: string;
  items?: MenuItem[];
}

const title = ref<string>("Management");
const items = ref<MenuItem[]>([
  {
    label: "Fleet",
    icon: "tabler:steering-wheel-filled",
    items: [
      {
        label: "Drivers",
        route: "/managements/fleet/drivers",
      },
      {
        label: "Vehicles",
        route: "/managements/fleet/vehicles",
      },
      {
        label: "Capabilities",
        route: "/managements/fleet/capabilities",
      },
    ],
  },
  {
    label: "Pricing",
    icon: "majesticons:pound-circle-line",
    items: [
      {
        label: "Tarrifs",
        route: "/managements/pricing/tarrifs",
      },
      {
        label: "Vehicles",
        route: "/managements/pricing/vehicles",
      },
      {
        label: "Capabilities",
        route: "/managements/pricing/capabilities",
      },
    ],
  },
  {
    label: "Settings",
    icon: "weui:setting-filled",
    items: [
      {
        label: "Accounts",
        route: "/managements/settings/manageAccounts",
      },
    ],
  },
]);
</script>
<style scoped>
.p-panelmenu-item-content {
  background: black !important;
  color: white !important;
}
</style>