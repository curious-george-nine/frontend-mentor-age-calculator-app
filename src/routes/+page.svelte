<script lang="ts">
  import Divider from "$lib/components/Divider.svelte";
  import Result from "$lib/components/Result.svelte";
  import Top from "$lib/components/Top.svelte";

  let dayValue: string;
  let monthValue: string;
  let yearValue: string;

  function handleDayInput(e: CustomEvent<any>) {
    dayValue = e.detail.dayValue;
    console.log(dayValue);
  }
  function handleMonthInput(e: CustomEvent<any>) {
    monthValue = e.detail.monthValue;
  }
  function handleYearInput(e: CustomEvent<any>) {
    yearValue = e.detail.yearValue;
  }
</script>

<div class="contents lg:block" />
<section class="pt-12 px-3 lg:col-span-3">
  <div class="bg-white px-8 rounded-3xl rounded-br-[6rem]">
    <Top
      on:dayInput={(e) => handleDayInput(e)}
      on:monthInput={(e) => handleMonthInput(e)}
      on:yearInput={(e) => handleYearInput(e)}
    />
    <Divider />
    <Result {dayValue} {monthValue} {yearValue} />
  </div>
</section>
