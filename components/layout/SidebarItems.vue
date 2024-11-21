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
            class="flex items-start !p-2 text-sm !text-black font-semibold !bg-neutral-300 !rounded-none"
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
              class="!p-3 !pl-[1.8rem] !bg-neutral-300"
            >
              <NuxtLink
                :to="link.route"
                class="text-black-600 font-bold hover:text-blue-800 w-100"
              >
                {{ link.name }}
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

<style scoped>
h1 {
  font-family: "Mitr", sans-serif;
}
</style>
