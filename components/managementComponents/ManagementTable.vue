<template>
  <ManagementHeader @search="handleSearch" />
  <div class="card">
    <DataTable :value="filteredProducts">
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
import { ref, computed, onMounted } from "vue";
import { ProductService } from "@/service/ProductService";
import ManagementHeader from "~/components/managementComponents/ManagementHeader.vue";

const products = ref([]);
const searchQuery = ref({
  searchByLocation: "",
  searchByCompany: "",
});

// Getting the products data from service folder
onMounted(() => {
  ProductService.getProductsMini().then((data) => (products.value = data));
});

// Updating search query
const handleSearch = (query) => {
  searchQuery.value = query;
};

// Filtering the products based on search query
const filteredProducts = computed(() => {
  return products.value.filter((product) => {
    const locationMatch = product.name
      ?.toLowerCase()
      .includes(searchQuery.value.searchByLocation.toLowerCase());
    const companyMatch = product.category
      ?.toLowerCase()
      .includes(searchQuery.value.searchByCompany.toLowerCase());
    return locationMatch && companyMatch;
  });
});
</script>
