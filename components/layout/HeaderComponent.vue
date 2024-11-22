<template>
  <header class="bg-black text-white px-4 pb-2 w-full">
    <div class="flex justify-between items-center">
      <NuxtImg
        src="/images/Logo.png"
        class="w-[10rem] pt-2"
        alt="Cabline Logo"
      />
      <nav>
        <ul class="flex items-baseline space-x-4 h-100">
          <li
            v-for="link in links"
            :key="link.path"
            class="relative hidden md:block h-12"
          >
            <NuxtLink
              :to="link.path"
              class="hover:text-gray-300 transition-colors duration-200 flex items-center space-x-2 pt-3"
              :style="
                route.path === link.path
                  ? 'border-top: 3px solid transparent; border-image: linear-gradient(90deg, #BB5DE9 0%, #30D5E8 100%); border-image-slice: 1;'
                  : ''
              "
            >
              <template v-if="link.path === '/user'">
                <Icon icon="raphael:user" />
              </template>
              <span>{{ link.name }}</span>
              <template v-if="link.path === '/user'">
                <Icon icon="mdi:arrow-down-drop" />
              </template>
            </NuxtLink>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script setup>
const route = useRoute();
const links = [
  { name: "Dispatch", path: "/dispatch" },
  { name: "Bookings", path: "/bookings" },
  { name: "Management", path: "/management" },
  { name: "Accounts", path: "/accounts" },
  { name: "Stats", path: "/stats" },
  { name: "User", path: "/user" },
];
</script>
