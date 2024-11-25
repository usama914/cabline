<template>
  <Dialog
    v-model:visible="isVisible"
    :header="header"
    :style="style"
    :modal="modal"
    @hide="onClose"
  >
    <slot />
  </Dialog>
</template>

<script setup lang="ts">
import { ref, watch, defineProps, defineEmits } from "vue";

// Define props for customization
const props = defineProps({
  header: {
    type: String,
    default: "Header",
  },
  style: {
    type: Object as () => Record<string, string>,
    default: () => ({ width: "50rem" }),
  },
  modal: {
    type: Boolean,
    default: true,
  },
  visible: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["update:visible", "close"]);

const isVisible = ref(props.visible);

watch(
  () => props.visible,
  (newVal) => {
    isVisible.value = newVal;
  }
);

const onClose = () => {
  emit("update:visible", false);
  emit("close");
};
</script>

<style scoped></style>
