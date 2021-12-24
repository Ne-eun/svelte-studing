<script lang="ts">
  import { Route, useNavigate, useLocation } from "svelte-navigator";
  import { user } from "./stores";

	const navigate = useNavigate();
  const location = useLocation();

  $: if (!$user) {
    navigate("/login", {
      state: { from: $location.pathname },
      replace: true,
    });
  }

  export let path: string;
</script>

<Route {path} let:params let:location let:navigate>
	{#if $user}
		<slot {params} {location} {navigate} />
	{/if}
</Route>