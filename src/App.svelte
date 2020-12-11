<script>
	import { Router, Route } from "svelte-routing";
	import Instructions from "./routes/Instructions.svelte"
	import Index from "./routes/Index.svelte"
</script>

<Router>
	<Route path="/" component={Index} />
	<Route path="/instructions" component={Instructions} />	
</Router>