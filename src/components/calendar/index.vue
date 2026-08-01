<template>
  <div class="flex space-x-5" v-bind="$attrs">
    <div class="flex flex-col grow">
      <Year @selected="changeYear" />
      <Month @selected="changeMonth" />
      <Dates :selectedValues :selectedDate />
    </div>
    <div class="w-1/2">
      <span v-if="selectedDate">
        You have selected <br />
        {{ `${selectedDate} ` }}
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
import dayjs from "dayjs";
import { defineAsyncComponent, ref, reactive } from "vue";

const Year = defineAsyncComponent(() => import("./Year.vue"));
const Month = defineAsyncComponent(() => import("./Month.vue"));
const Dates = defineAsyncComponent(() => import("./Dates.vue"));

const selectedDate = ref(dayjs().date());

const selectedValues = reactive({
  month: dayjs().month(),
  year: dayjs().year(),
});

function changeMonth(v: number) {
  selectedValues.month = v;
}

function changeYear(v: number) {
  selectedValues.year = v;
}
</script>

<style scoped></style>
