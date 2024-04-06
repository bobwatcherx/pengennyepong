<script>
  import { Router,Route } from "svelte-navigator";
  import Home from "./pages/Home.svelte";
  import Player from "./pages/Player.svelte";
</script>

<Router>
  <div>
    <Route path="/">
      <Home />
    </Route>
    <Route path="player/:id" let:params>
      <Player id={params.id} />
    </Route>
  </div>
</Router>