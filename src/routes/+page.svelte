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
    <button class="px-4 py-2 border flex gap-2 border-slate-200 rounded-lg text-slate-700 hover:border-slate-400  hover:text-slate-900 hover:shadow transition duration-150" on:click={() => signIn("github")}>
      <img class="w-6 h-6" src="https://www.svgrepo.com/show/361181/github.svg" loading="lazy" alt="github logo">
      <span>Login with Github</span>
    </button>
    <button class="px-4 py-2 border flex gap-2 border-slate-200 rounded-lg text-slate-700 hover:border-slate-400  hover:text-slate-900 hover:shadow transition duration-150" on:click={() => signIn("google")}>
      <img class="w-6 h-6" src="https://www.svgrepo.com/show/475656/google-color.svg" loading="lazy" alt="google logo">
      <span>Login with Google</span>
    </button>
  {/if}
</div>

