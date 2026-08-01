<template>
  <div class="flex space-x-5" v-bind="$attrs">
    <div class="flex flex-col grow">
      <Year />
      <Month />
      <Dates />
    </div>
    <div class="w-1/2">
      <span v-if="selectedDateValue">
        You have selected <br />
        {{ `${selectedDateValue} ` }}
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
import dayjs from "dayjs";
import { defineAsyncComponent, ref } from "vue";

const Year = defineAsyncComponent(() => import("./Year.vue"));
const Month = defineAsyncComponent(() => import("./Month.vue"));
const Dates = defineAsyncComponent(() => import("./Dates.vue"));

const selectedDateValue = ref(dayjs().date());
</script>

<style scoped></style>
