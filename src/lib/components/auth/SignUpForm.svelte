<script lang="ts">
  import { enhance } from "$app/forms";
  import SubmitButton from "./SubmitButton.svelte";

  let { error, message } = $props();
</script>

<form
  class="flex flex-col w-full"
  method="post"
  action="?/signUp"
  use:enhance
>
  {#if error || message}
    <div
      class={`${
        error ? "bg-rose-100 text-rose-950" : "bg-sky-200 text-sky-950"
      } px-4 py-3 rounded-md mb-3`}
    >
      {error || message}
    </div>
  {/if}

  <label for="email" class="font-medium text-sm mb-1 ml-2"> Email </label>
  <input
    autocomplete="email"
    type="email"
    id="email"
    name="email"
    required
    class="border border-slate-200 rounded-lg mb-4 px-4 py-3 outline-teal-600 outline-2 focus:outline "
  />
  <label for="password" class="font-medium text-sm mb-1 ml-2"> Password </label>
  <input
    autocomplete="current-password"
    type="password"
    id="password"
    name="password"
    required
    class="border border-slate-200 rounded-lg mb-4 px-4 py-3 outline-teal-600 outline-2 focus:outline "
  />
  <SubmitButton label="Sign up" />

  <div class="text-slate-500 mt-3">
    Already have an account?{" "}
    <a href="/identity/signin" class="text-teal-600 hover:text-teal-700">
      Sign in
    </a>
  </div>
</form>
