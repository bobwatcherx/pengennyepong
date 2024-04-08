<script>
  import { Router,Route } from "svelte-navigator";
  import Home from "./pages/Home.svelte";
  import Player from "./pages/Player.svelte";
  import Jav from "./pages/Jav.svelte";
    import Navbarmenu from './lib/Navbarmenu.svelte'


</script>

<Router>
  <div>
    <Navbarmenu/>
    <Route path="/">
      <Home />
    </Route>
    <Route path="player/:id" let:params>
      <Player id={params.id} />
    </Route>
    <Route path="jav/:id/:title" let:params>
      <Jav javid={params.id} javtitle={params.title}/>
    </Route>
  </div>
</Router>