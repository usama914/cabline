<template>
  <div class="button-group">
    <Button
      v-if="$slots.primary"
      label="new"
      severity="help"
      class="px-5"
    >
      <slot name="primary">Primary Button</slot></Button
    >

    <Button
      v-if="$slots.secondary"
      label="new"
      severity="contrast"
      class="px-5"
    >
      <slot name="secondary">Secondary Button</slot></Button
    >
  </div>
</template>

<script setup></script>