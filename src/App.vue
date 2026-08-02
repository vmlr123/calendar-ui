<script setup lang="ts">
import { defineAsyncComponent } from "vue";

const Calendar = defineAsyncComponent(
  () => import("./components/calendar/index.vue"),
);
</script>

<template>
  <div class="max-w-2xl mx-auto mt-1 justify-center">
    <Calendar class="w-full" />
  </div>
</template>

<style scoped></style>
