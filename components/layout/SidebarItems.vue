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
          :model="items"
          class="w-full md:w-80"
          style="
            --p-panelmenu-panel-background: var(--color-neutral-light) !important;
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
  url?: string;
  target?: "_blank" | "_self";
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
        icon: "pi pi-eraser",
        route: "/management/fleet/drivers",
      },
      {
        label: "Vehicles",
        icon: "pi pi-heart",
        route: "/management/fleet/vehicles",
      },
      {
        label: "Capabilities",
        icon: "pi pi-heart",
        route: "/management/fleet/capabilities",
      },
    ],
  },
  {
    label: "Pricing",
    icon: "majesticons:pound-circle-line",
    items: [
      {
        label: "Tarrifs",
        icon: "pi pi-star",
        route: "/management/pricing/tarrifs",
      },
      {
        label: "Vehicles",
        icon: "pi pi-bookmark",
        route: "/management/pricing/vehicles",
      },
      {
        label: "Capabilities",
        icon: "pi pi-bookmark",
        route: "/management/pricing/capabilities",
      },
    ],
  },
  {
    label: "Settings",
    icon: "weui:setting-filled",
    items: [
      {
        label: "Accounts",
        icon: "pi pi-star",
        route: "/management/settings/manageAccounts",
      },
    ],
  },
]);
</script>
