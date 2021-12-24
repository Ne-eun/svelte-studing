<script lang="ts">
	import { Router, Route, Link } from "svelte-navigator";
	import { user } from "./stores";

	import { Login } from "./pages/login/Login";
	import { Test } from "./Test.svelte"
</script>

<Router>
  <main>
    <Route path="login">
      <Login />
    </Route>

    <Route path="/">
      <Test />
    </Route>

    <PrivateRoute path="/" let:location>
      <h3>Welcome {$user.username}</h3>
      <button on:click={handleLogout}>Logout</button>
    </PrivateRoute>
  </main>
</Router>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>