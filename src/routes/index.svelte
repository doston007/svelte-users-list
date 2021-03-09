<script context="module">
  export async function preload(page) {
    const res = await this.fetch("https://jsonplaceholder.typicode.com/users");
    const users = await res.json();

    return { users };
  }
</script>

<script>
  import UserCard from "../components/UserCard.svelte";
  import SearchInput from "../components/SearchInput.svelte";

  export let users;
  let search = "";
  $: searchedUsers = [...users].filter((user) =>
    search
      .toLowerCase()
      .split(" ")
      .every((v) => user.name.toString().toLowerCase().includes(v))
  );
</script>

<svelte:head>
  <title>Users list</title>
</svelte:head>

<SearchInput bind:value={search} placeholder="Search by user's name" />
{#each searchedUsers as user}
  <UserCard {user} />
{/each}
