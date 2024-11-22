<template>
  <header class="bg-black text-white px-4 pb-2 w-full relative">
    <div class="flex justify-between items-center">
      <NuxtImg
        src="/images/Logo.png"
        class="w-[10rem] pt-2"
        alt="Cabline Logo"
      />
      <!-- Desktop Menu -->
      <nav class="hidden md:block">
        <ul class="flex items-baseline space-x-4 h-100">
          <li v-for="link in links" :key="link.path" class="relative h-12">
            <NuxtLink
              :to="link.path"
              class="hover:text-gray-300 transition-colors duration-200 flex items-center space-x-2 pt-3"
              :style="
                route.path === link.path
                  ? 'border-top: 3px solid transparent; border-image: linear-gradient(90deg, #BB5DE9 0%, #30D5E8 100%); border-image-slice: 1;'
                  : ''
              "
            >
              <template v-if="link.path === '/profile'">
                <Icon icon="raphael:user" />
              </template>
              <span>{{ link.name }}</span>
              <template v-if="link.path === '/profile'">
                <Icon icon="mdi:arrow-down-drop" />
              </template>
            </NuxtLink>
          </li>
        </ul>
      </nav>
      <!-- Mobile Menu Icon -->
      <div class="block md:hidden">
        <Icon
          icon="material-symbols:menu"
          class="cursor-pointer w-[2rem] h-[1.5rem]"
          @click="toggleMenu"
        />
      </div>
    </div>

    <!-- Mobile Menu -->
    <div
      class="absolute top-0 left-0 w-full h-full bg-black text-white z-50 transform transition-transform duration-300"
      :class="{
        'translate-x-0': isMobileMenuOpen,
        '-translate-x-full': !isMobileMenuOpen,
      }"
    >
      <div class="flex justify-between items-center px-4 pt-4 pb-[.5rem]">
        <NuxtImg src="/images/Logo.png" class="w-[8rem]" alt="Cabline Logo" />
        <Icon
          icon="material-symbols:close"
          class="cursor-pointer w-[2rem] h-[1.5rem]"
          @click="closeMenu"
        />
      </div>
      <Divider class="!p-0 !m-0" />
      <ul class="flex flex-col items-start space-y-4 px-6 p-3 bg-black">
        <li v-for="link in links" :key="link.path">
          <NuxtLink
            :to="link.path"
            class="block text-lg hover:bg-gray-700 px-3 py-2 rounded transition w-full"
            @click="closeMenu"
            :style="
              route.path === link.path
                ? 'border-top: 3px solid transparent; border-image: linear-gradient(90deg, #BB5DE9 0%, #30D5E8 100%); border-image-slice: 1;'
                : ''
            "
          >
            <span>{{ link.name }}</span>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useRoute } from "vue-router";

interface Link {
  name: string;
  path: string;
}

const route = useRoute();
const links: Link[] = [
  { name: "Dispatch", path: "/" },
  { name: "Bookings", path: "/bookings" },
  { name: "Management", path: "/management" },
  { name: "Accounts", path: "/accounts" },
  { name: "Stats", path: "/stats" },
  { name: "Profile", path: "/profile" },
];

// Mobile menu toggle
const isMobileMenuOpen = ref(false);
const toggleMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
const closeMenu = () => {
  isMobileMenuOpen.value = false;
};
</script>
