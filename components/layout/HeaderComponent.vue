<template>
  <header class="bg-black text-white px-4 pb-2 w-full">
    <div class="flex justify-between items-center">
      <NuxtImg
        src="/images/Logo.png"
        class="w-[10rem] pt-2"
        alt="Cabline Logo"
      />
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
      <nav class="block md:hidden">
        <Icon
          icon="material-symbols:menu"
          class="cursor-pointer w-[2rem] h-[1.5rem]"
        />
      </nav>
    </div>
  </header>
</template>

<script setup lang="ts">
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
</script>
