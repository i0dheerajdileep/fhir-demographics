<script>
  import { onMount } from "svelte";
  import { fhir } from "./fhir";
  import {Link} from "svelte-routing"

    let data = []
    onMount(async ()=>{
       const r =  await fhir.get('/Patient')
       console.log(r)
       data = r.data?.entry
    })
</script>
<div class="p-10">
    <h1 class="text-3xl font-sans font-bold">Patients</h1>
    <div class="mt-10">
        {#each data as patient}
            <Link to={`patient/${patient.resource.id}`}  class="bg-gray-200 shadow-md px-24 py-4 text-left text-blue-500">{patient.resource.name[0].given}</Link>
        {/each}
    </div>
</div>