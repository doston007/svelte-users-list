<script context="module">
  export async function preload(page) {
    const { user } = page.params;

    const res = await this.fetch(
      "https://jsonplaceholder.typicode.com/users/" + user
    );
    const singleUser = await res.json();

    return { singleUser };
  }
</script>

<script>
  import UserCard from "../components/UserCard.svelte";

  export let singleUser;
</script>

<svelte:head>
  <title>{ singleUser.name }</title>
</svelte:head>

<a href="." class="bg-grey hover:bg-grey-dark font-bold py-2 px-4 rounded-r rounded-lg shadow">Users list</a>
<UserCard user={singleUser} />
