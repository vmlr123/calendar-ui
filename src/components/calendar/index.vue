<template>
  <div class="flex flex-col space-x-5 justify-center" v-bind="$attrs">
    <div class="flex flex-col grow justify-center mx-auto max-w-2xl">
      <Year @selected="changeYear" />
      <Month @selected="changeMonth" />
      <Dates :selectedValues :selectedDate @selected="changeDate" />
    </div>
    <div class="w-1/4 mt-2 mx-auto justify-center text-center">
      <span v-if="selectedDate" class="text-center justify-center mx-auto">
        You have selected <br />
        {{
          `${selectedValues.month + 1} - ${selectedDate} - ${selectedValues.year}`
        }}
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

const selectedDate = ref<number | null>(dayjs().date());

const selectedValues = reactive({
  month: dayjs().month(),
  year: dayjs().year(),
});

function changeMonth(v: number) {
  selectedDate.value = null;
  selectedValues.month = v;
}

function changeYear(v: number) {
  selectedDate.value = null;
  selectedValues.year = v;
}

function changeDate(v: number) {
  selectedDate.value = v;
}
</script>

<style scoped></style>
