<template>
  <header
    class="bg-white text-black flex flex-col items-start gap-8 py-2 mb-2 xl:flex-row xl:justify-between xl:items-center"
  >
    <div class="tarrifs flex flex-col justify-start items-start space-y-2">
      <div class="card flex justify-center">
        <Breadcrumb
          class="font-mitr text-xs !p-0 uppercase tracking-widest"
          :model="items"
        >
          <template #item="{ item }">
            <span>{{ item.label }} </span>
          </template>
          <template #separator>
            <Icon icon="material-symbols:play-arrow" class="w-5 h-5" />
          </template>
        </Breadcrumb>
      </div>
      <div class="heading">
        <h1 class="font-mitr text-xl uppercase tracking-widest">
          {{ heading }}
        </h1>
      </div>
      <div class="results">
        <p class="font-mitr text-xs uppercase tracking-widest">
          {{ results }} Results Found
        </p>
      </div>
    </div>
    <div class="actions flex gap-3 flex-wrap">
      <IconField>
        <InputIcon> <Icon icon="iconamoon:search-light" /> </InputIcon>
        <InputText
          class="w-[14rem] md:w-[22rem]"
          type="text"
          placeholder="Search by Tariffs, Pickup and Destination"
          v-model="searchByLocation"
          @input="emitSearch"
        />
      </IconField>
      <IconField>
        <InputIcon> <Icon icon="iconamoon:search-light" /> </InputIcon>
        <InputText
          class="w-[14rem]"
          type="text"
          placeholder="Search by Company"
          v-model="searchByCompany"
          @input="emitSearch"
        />
      </IconField>
      <ButtonGroup>
        <template #primary> New <Icon icon="prime:check" /></template>
      </ButtonGroup>
    </div>
  </header>
</template>

<script setup lang="ts">
import ButtonGroup from "~/components/base/ButtonGroup.vue";
import { ref } from "vue";

// Defining the variables with their types
const heading: string = "Tariffs";
const results: number = 20;
const items = ref<{ label: string }[]>([{ label: "Pricing" }, { label: "Tariff" }]);

const searchByLocation = ref<string>("");
const searchByCompany = ref<string>("");

// Defining the emit function to handle the search event
const emit = defineEmits(["search"]);

const emitSearch = (): void => {
  emit("search", {
    searchByLocation: searchByLocation.value,
    searchByCompany: searchByCompany.value,
  });
};
</script>

<style scoped>
/* Add any scoped styles if necessary */
</style>
