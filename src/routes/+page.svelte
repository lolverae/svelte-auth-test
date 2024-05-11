<script lang="ts">
  import { signIn, signOut } from "@auth/sveltekit/client";

  import { page } from "$app/stores";
  console.log($page.data.session)
</script>

<div class="p-20">
  {#if $page.data.session}
    <h1>Logged in</h1>
    <h2>Hello {$page.data.session.user?.name}</h2>
      <img alt="User Profile" src={$page.data.session.user?.image} />
  {:else}
    <h1>Not logged in</h1>
    <button on:click={() => signIn("github")}>Sign In</button>
  {/if}
</div>
