<script>
  export let placeholder = "Search...";
  export let value = "";
</script>

<input
  type="text"
  class="relative outline-none rounded py-3 px-3 w-full bg-white shadow text-sm text-gray-700 placeholder-gray-400 focus:outline-none focus:shadow-outline"
  {placeholder}
  bind:value
/>
