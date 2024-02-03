<script>
  import { onMount } from "svelte";
    import { fhir } from "./fhir";
    let loading = false
    export let id;
    let form;
    console.log(id)
    async function handleSubmit(e){
      // console.log(e.detail)
      if(id){
        loading = true
        const r = await fhir.put(`/Patient/${id}`,{...e.detail,id: id})
        console.log(r.data)
        loading = false
      }else{
          loading = true
          const r = await fhir.post("/Patient",e.detail)
          console.log(r.data)
          loading = false
      }
    }

    onMount(async()=>{
        if(id){
           const r = await fhir.get(`/Patient/${id}`)
           const resource = r.data
           form.import(resource)
        }
    })
  
  </script>
  <div>
    <div class="mt-10">
      <h1 class="text-4xl font-semibold font-sans">Patient registration</h1>
      <mb-fhir-form class="mt-10" on:mb-submit={handleSubmit} bind:this={form}>
        <mb-context path="resourceType" bind="Patient"></mb-context>
        <mb-input path="name[0].given" label="Name"/>
        <mb-date label="Date of birth" path="birthDate"/>
        <mb-buttons datatype="code" label="Gender" path="gender">
          <mb-option value="male" label="Male"></mb-option>
          <mb-option value="female" label="Female"></mb-option>
          <mb-option value="other" label="Other"></mb-option>
        </mb-buttons>
        <mb-submit>
          <sl-button {loading} type="info">Register</sl-button>
        </mb-submit>
      </mb-fhir-form>
  
    </div>
  
  </div>