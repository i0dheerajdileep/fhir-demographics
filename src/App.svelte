<script>
  import "medblocks-ui"
  import "medblocks-ui/dist/styles.js"
  import "medblocks-ui/dist/shoelace" 
  import {Router, Route, Link} from "svelte-routing"
  import PatientReg from "./PatientReg.svelte";
  import Layout from "./Layout.svelte";
</script>
<div>
  <Router>
    <Layout>
      <Route path="/patient" component={PatientReg} />
      <Route path="/" >List</Route>
    </Layout>
  </Router>
</div>