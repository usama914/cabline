<template>
  <header class="bg-black text-white px-4 w-full relative">
    <div class="flex justify-between items-center">
      <NuxtImg
        src="/images/Logo.png"
        class="w-[7.5rem] pt-2"
        alt="Cabline Logo"
      />
      <!-- Desktop Menu -->
      <nav class="hidden md:block">
        <ul class="flex items-baseline space-x-4 h-100">
          <li v-for="link in links" :key="link.path" class="relative h-12">
            <template v-if="link.path === '/profile'">
              <div
                class="hover:text-gray-300 transition-colors duration-200 flex items-center space-x-2 pt-3 cursor-pointer"
                @click="toggle"
                aria-haspopup="true"
                aria-controls="profile_menu"
              >
                <Icon icon="raphael:user" class="h-[12px]" />
                <span>{{ link.name }}</span>
                <Icon icon="mdi:arrow-down-drop" class="h-[12px]" />
              </div>
            </template>
            <template v-else>
              <NuxtLink
                :to="link.path"
                class="hover:text-gray-300 transition-colors duration-200 flex items-center space-x-2 pt-3"
                :style="route.path === link.path ? activeStyle : ''"
              >
                <span>{{ link.name }}</span>
              </NuxtLink>
            </template>
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

    <!-- Pop-up Menu -->
    <Menu ref="menu" id="profile_menu" :model="menuItems" :popup="true">
      <template #item="{ item }">
        <NuxtLink :to="item.route">
          <div class="flex items-center justify-start mb-2 cursor-pointer p-2">
            <Icon :icon="item.icon" />
            <span class="ml-2">{{ item.label }}</span>
          </div>
        </NuxtLink>
      </template>
    </Menu>

    <!-- Mobile Menu -->
    <div
      class="absolute top-0 left-0 w-full bg-black h-full text-white z-50 transform transition-transform duration-300"
      :class="{
        'translate-x-0': isMobileMenuOpen,
        '-translate-x-full': !isMobileMenuOpen,
      }"
    >
      <div class="flex justify-between items-center px-4 h-[3rem] bg-black">
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
            :style="route.path === link.path ? activeStyle : ''"
          >
            <span>{{ link.name }}</span>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </header>
</template>
<script setup lang="ts">
import { ref, onMounted, onUnmounted, watch } from "vue";
import { useRoute } from "vue-router";

interface Link {
  name: string;
  path: string;
}

const route = useRoute();
const activeStyle =
  "border-top: 3px solid transparent; border-image: linear-gradient(90deg, #BB5DE9 0%, #30D5E8 100%); border-image-slice: 1;";
const links: Link[] = [
  { name: "Dispatch", path: "/dispatch" },
  { name: "Bookings", path: "/bookings" },
  { name: "Management", path: "/management" },
  { name: "Accounts", path: "/accounts" },
  { name: "Stats", path: "/stats" },
  { name: "Profile", path: "/profile" },
];

// Mobile menu toggle
const isMobileMenuOpen = ref(false);
const screenWidth = ref(0);

const toggleMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const closeMenu = () => {
  isMobileMenuOpen.value = false;
};

// Update screen width on resize
const updateScreenWidth = () => {
  if (process.client) {
    screenWidth.value = window.innerWidth;
  }
};

// Watching for screen size changes
watch(screenWidth, (newWidth) => {
  if (newWidth >= 768) {
    isMobileMenuOpen.value = false; // Close menu for desktop
  }
});

onMounted(() => {
  if (process.client) {
    screenWidth.value = window.innerWidth;
    window.addEventListener("resize", updateScreenWidth);
  }
});

onUnmounted(() => {
  if (process.client) {
    window.removeEventListener("resize", updateScreenWidth);
  }
});

// Pop-up menu toggle
const menu = ref();
const menuItems = ref([
  {
    label: "My Profile",
    icon: "raphael:user",
    route: "/management/settings/manageAccounts",
  },
  { label: "Logout", icon: "material-symbols:logout", route: "/" },
]);

const toggle = (event: MouseEvent) => {
  menu.value.toggle(event);
};
</script>
