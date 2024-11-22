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

<script setup lang="ts">
import { ref, computed, onMounted } from "vue";
import { ProductService } from "~/service/ProductService";
import ManagementHeader from "~/components/managementComponents/ManagementHeader.vue";

// Definning types for product and search query
interface Product {
  id: number;
  name: string;
  code: string;
  description: string;
  category: string;
  quantity: number;
  rating: number;
}

interface SearchQuery {
  searchByLocation: string;
  searchByCompany: string;
}

// Reactive references
const products = ref<Product[]>([]);
const searchQuery = ref<SearchQuery>({
  searchByLocation: "",
  searchByCompany: "",
});

// Getting the products data from the service
onMounted(() => {
  ProductService.getProductsMini().then((data) => (products.value = data));
});

// Defining emits and their types
const emit = defineEmits<{
  (e: "search", query: SearchQuery): void;
}>();

// Updating search query received from ManagementHeader component
const handleSearch = (query: SearchQuery): void => {
  searchQuery.value = query;
  emit("search", query); // Emit the updated search query to parent component (if necessary)
};

// Filter the products based on the search query
const filteredProducts = computed(() => {
  return products.value.filter((product) => {
    const locationMatch = product.name
      .toLowerCase()
      .includes(searchQuery.value.searchByLocation.toLowerCase());
    const companyMatch = product.category
      .toLowerCase()
      .includes(searchQuery.value.searchByCompany.toLowerCase());
    return locationMatch && companyMatch;
  });
});
</script>

<style scoped></style>
