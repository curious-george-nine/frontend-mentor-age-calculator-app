<script lang="ts">
  import TopInput from "./TopInput.svelte";
  import { createEventDispatcher } from "svelte";

  let dayValue, monthValue, yearValue: string;

  const dispatch = createEventDispatcher();

  function handleDayInput(e: CustomEvent<string>) {
    dayValue = e.detail.dayValue;

    dispatch("dayInput", { dayValue: dayValue });
  }

  function handleMonthInput(e: CustomEvent<string>) {
    monthValue = e.detail.monthValue;

    dispatch("monthInput", { monthValue: monthValue });
  }

  function handleYearInput(e: CustomEvent<string>) {
    yearValue = e.detail.yearValue;

    dispatch("yearInput", { yearValue: yearValue });
  }
</script>

<div class="grid grid-cols-3 gap-6 pt-10 pb-16 lg:w-3/4">
  <div><TopInput label="day" on:input={(e) => handleDayInput(e)} /></div>
  <div><TopInput label="month" on:input={(e) => handleMonthInput(e)} /></div>
  <div><TopInput label="year" on:input={(e) => handleYearInput(e)} /></div>
</div>
