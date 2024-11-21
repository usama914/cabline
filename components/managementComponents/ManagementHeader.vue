<template>
  <header
    class="bg-white text-black flex flex-col items-start gap-8 px-4 py-2 mb-2 xl:flex-row xl:justify-between xl:items-center"
  >
    <div class="tarrifs flex flex-col justify-start items-start space-y-2">
      <div class="card flex justify-center">
        <Breadcrumb
          class="text-xs !p-0 uppercase tracking-widest"
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
        <h1 class="text-xl uppercase tracking-widest">
          {{ heading }}
        </h1>
      </div>
      <div class="results">
        <p class="text-xs uppercase tracking-widest">
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
          placeholder="Search by Tariffs, Pickup and  Destination"
        />
      </IconField>
      <IconField>
        <InputIcon> <Icon icon="iconamoon:search-light" /> </InputIcon>
        <InputText
          class="w-[14rem]"
          type="text"
          placeholder="Search by Company"
        />
      </IconField>
      <ButtonGroup>
        <template #primary> New <Icon icon="prime:check" /></template>
      </ButtonGroup>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
import ButtonGroup from "~/components/base/ButtonGroup.vue";

const heading = "Tarrifs";
const results = 20;
const items = ref([{ label: "Pricing" }, { label: "Tarrif" }]);
</script>
<style scoped>
.p-breadcrumb,
h1,
p {
  font-family: "Mitr", sans-serif;
}
</style>
