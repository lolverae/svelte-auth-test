<script lang="ts">
  import { signIn, signOut } from "@auth/sveltekit/client";

  import { page } from "$app/stores";
  console.log($page.data.session);
</script>

<div class="container mx-auto px-4 py-8 bg-gray-100">
  {#if $page.data.session}
    <h1 class="text-3xl font-bold text-green-500 mb-4">Logged in</h1>
    <div class="flex items-center space-x-4">
      <h2 class="text-xl font-medium text-gray-800">Hello, {$page.data.session.user?.name}</h2>
      <img
        class="w-16 h-16 rounded-full object-cover"
        alt="User Profile"
        src={$page.data.session.user?.image}
      />
    </div>
    <button type="button" class="btn btn-primary bg-blue-100 rounded-full text-lg p-2" on:click={() => signOut()}>
      Sign Out
    </button>
  {:else}
    <h1 class="text-3xl font-bold text-blue-500 mb-4">Not logged in</h1>
    <button type="button" class="btn btn-secondary bg-blue-100 rounded-full text-lg p-2" on:click={() => signIn("github")}>
      Sign In with GitHub
    </button>
    <button type="button" class="btn btn-secondary bg-blue-100 rounded-full text-lg p-2" on:click={() => signIn("google")}>
      Sign In with Google
    </button>
  {/if}
</div>

