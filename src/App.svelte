<script>
  import "medblocks-ui"
  import "medblocks-ui/dist/styles.js"
  import "medblocks-ui/dist/shoelace" 
  import {Router, Route, Link} from "svelte-routing"
  import PatientReg from "./PatientReg.svelte";
  import Layout from "./Layout.svelte";
  import List from "./List.svelte";
</script>
<div>
  <Router>
    <Layout>
      <Route path="/" component={List}></Route>
      <Route path="/patient" component={PatientReg} />
      <Route path="/patient/:id" component={PatientReg} />
    </Layout>
  </Router>
</div>