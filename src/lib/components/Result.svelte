<script lang="ts">
  export let dayValue: string;
  export let monthValue: string;
  export let yearValue: string;

  $: console.log(dayValue);
  $: console.log(monthValue);
  $: console.log(yearValue);

  $: diff = Math.abs(
    // @ts-ignore
    new Date() - new Date(`${yearValue}/${monthValue}/${dayValue}`)
  );

  $: console.log(new Date(diff).getFullYear());
  console.log(new Date());
</script>

<div class="pt-16 pb-10 italic font-bold text-5xl">
  <p>
    <span class="text-violet-500"
      >{Number.isNaN(diff) ? "- -" : new Date(diff).getFullYear() - 1970}</span
    >
    years
  </p>
  <p>
    <span class="text-violet-500"
      >{Number.isNaN(diff) ? "- -" : new Date(diff).getMonth() + 1}</span
    > months
  </p>
  <p>
    <span class="text-violet-500"
      >{Number.isNaN(diff) ? "- -" : new Date(diff).getDate()}</span
    > days
  </p>
</div>
