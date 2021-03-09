<script>
  export let user;
  $: userKeys = Object.keys(user);
  $: userKeysCapitalized = userKeys.map(
    (key) => key.charAt(0).toUpperCase() + key.slice(1)
  );
</script>

<a
  href={`/${user.id}`}
  class="rounded block overflow-hidden shadow-lg hover:shadow-xl p-4 mb-4 transition duration-300"
>
  {#each userKeys as key, i}
    <div>
      <strong>{userKeysCapitalized[i]}</strong>: {JSON.stringify(user[key])}
    </div>
  {/each}
</a>
