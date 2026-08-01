<script setup lang="ts">
import { defineAsyncComponent } from "vue";

const Calendar = defineAsyncComponent(
  () => import("./components/calendar/index.vue"),
);
</script>

<template>
  <div class="max-w-2xl mx-auto py-16">
    <Calendar />
  </div>
</template>

<style scoped></style>
