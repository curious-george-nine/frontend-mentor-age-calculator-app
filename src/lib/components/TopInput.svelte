<script lang="ts">
  export let label: "day" | "month" | "year";

  let placeholder: "DD" | "MM" | "YYYY" | undefined =
    label == "day"
      ? "DD"
      : label == "month"
      ? "MM"
      : label == "year"
      ? "YYYY"
      : undefined;

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  let value: string;

  function handleInputEvent(): void {
    interface details {
      dayValue?: string;
      monthValue?: string;
      yearValue?: string;
    }

    let details: details = {};

    details[`${label}Value`] = value;

    switch (label) {
      case "day":
        if (Number(value) <= 31 && Number(value) >= 1) {
          dispatch("input", details);
        }
        break;
      case "month":
        if (Number(value) <= 12 && Number(value) >= 1) {
          dispatch("input", details);
        }
        break;
      case "year":
        dispatch("input", details);
    }

    console.log(details);
    // dispatch("input", details);
  }
</script>

<label
  for="label"
  class="uppercase tracking-widest text-gray-600 text-sm mb-2 block"
  >{label}</label
>
<input
  type="text"
  id={label}
  class="w-24 border-gray-400 border rounded p-3 focus:outline-none"
  bind:value
  on:input={handleInputEvent}
  {placeholder}
/>
