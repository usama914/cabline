<template>
  <div class="card">
    <DataTable :value="products" >
      <Column field="id" header="ID"></Column>
      <Column field="name" header="Name"></Column>
      <Column field="code" header="Code"></Column>
      <Column field="description" header="Description"></Column>
      <Column field="category" header="Category"></Column>
      <Column field="quantity" header="Quantity"></Column>
      <Column field="rating" header="Rating"></Column>
    </DataTable>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { ProductService } from "@/service/ProductService";

onMounted(() => {
  ProductService.getProductsMini().then((data) => (products.value = data));
});

const products = ref();
</script>

<style scoped></style>
