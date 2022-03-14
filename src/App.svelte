<script lang="ts">
  import "./index.css";

  import { Router, Route, Link, navigate } from "svelte-routing";
  import Dashboard from "./lib/Dashboard.svelte";
  import Home from "./lib/Home.svelte";
  import Login from "./lib/Login.svelte";

  import user from "./store";

  let url = "";

  $: if (!$user) {
    navigate("/login");
  }
</script>

<Router {url}>
  {#if $user}
    <nav>
      <ul>
        <Link to="/">Home</Link>
        <Link to="dashboard">dashboard</Link>
      </ul>
    </nav>
    <Route path="/" component={Home} />
    <Route path="/dashboard" component={Dashboard} />
  {:else}
    <Route path="/login" component={Login} />
  {/if}
</Router>
