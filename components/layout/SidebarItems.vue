<!-- Here in the sidebar all the content ( Heading , Links etc) will be changed based on the route we are at -- Functionality and Component postion Pending -->

<template>
  <div
    class="h-100 w-60 flex-col items-center pt-5 hidden lg:flex"
    :style="{ backgroundColor: 'var(--color-neutral-semilight)' }"
  >
    <div class="w-48">
      <div class="title mb-4">
        <h1 class="text-base uppercase tracking-widest">{{ title }}</h1>
      </div>
      <Accordion value="0" class="border-none">
        <AccordionPanel
          v-for="tab in tabs"
          :key="tab.title"
          :value="tab.value"
          class="mb-2"
        >
          <AccordionHeader
            class="flex items-start p-2 text-sm !text-black font-semibold !bg-neutral-300 rounded"
          >
            <div class="flex items-center gap-1">
              <Icon :icon="getIcon(tab.title)" />
              {{ tab.title }}
            </div>
          </AccordionHeader>
          <AccordionContent
            class="text-sm text-gray-600"
            style="--p-accordion-content-padding: 0px !important"
          >
            <div
              v-for="link in tab.links"
              :key="link.name"
              class="p-3 pl-7 bg-neutral-300"
            >
              <NuxtLink
                :to="link.route"
                class="block font-bold w-full py-1 px-1 rounded hover:bg-black"
                :class="{
                  'text-white bg-black': route.path === link.route,
                  'text-gray-600 hover:text-white': route.path !== link.route,
                }"
              >
                <span>
                  {{ link.name }}
                </span>
              </NuxtLink>
            </div>
          </AccordionContent>
        </AccordionPanel>
      </Accordion>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const route = useRoute();

const title = "Management";
const tabs = ref([
  {
    title: "Fleet",
    value: "0",
    links: [
      { name: "Drivers", route: "/drivers" },
      { name: "Vehicles", route: "/vehicles" },
      { name: "Capabilities", route: "/capabilities" },
    ],
  },
  {
    title: "Pricing",
    value: "1",
    links: [
      { name: "Tariffs", route: "/tariffs" },
      { name: "Vehicles", route: "/vehicles" },
      { name: "Capabilities", route: "/capabilities" },
    ],
  },
  {
    title: "Settings",
    value: "2",
    links: [{ name: "Settings", route: "/settings" }],
  },
]);

const getIcon = (title) => {
  switch (title) {
    case "Fleet":
      return "tabler:steering-wheel-filled";
    case "Pricing":
      return "majesticons:pound-circle-line";
    case "Settings":
      return "weui:setting-filled";
    default:
      return "";
  }
};
</script>
