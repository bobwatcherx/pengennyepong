<script>
  import { Router,Route } from "svelte-navigator";
  import Home from "./pages/Home.svelte";
  import Player from "./pages/Player.svelte";
  import Jav from "./pages/Jav.svelte";
</script>

<Router>
  <div>
    <Route path="/">
      <Home />
    </Route>
    <Route path="player/:id" let:params>
      <Player id={params.id} />
    </Route>
    <Route path="jav/:id" let:params>
      <Jav javid={params.id} />
    </Route>
  </div>
</Router>