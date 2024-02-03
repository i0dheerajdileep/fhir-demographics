<script>
    import axios from "axios"
  
    async function handleSubmit(e){
      // console.log(e.detail)
      const r = await axios.post("http://localhost:8090/fhir/Patient",e.detail)
      console.log(r.data)
    }
  
  </script>
  <div>
    <div class="mt-10">
      <h1 class="text-4xl font-semibold font-sans">Patient registration</h1>
      <mb-fhir-form class="mt-10" on:mb-submit={handleSubmit}>
        <mb-context path="resourceType" bind="Patient"></mb-context>
        <mb-input path="name[0].given" label="Name"/>
        <mb-date label="Date of birth" path="birthDate"/>
        <mb-buttons datatype="code" label="Gender" path="gender">
          <mb-option value="male" label="Male"></mb-option>
          <mb-option value="female" label="Female"></mb-option>
          <mb-option value="other" label="Other"></mb-option>
        </mb-buttons>
        <mb-submit>
          <sl-button type="info">Register</sl-button>
        </mb-submit>
      </mb-fhir-form>
  
    </div>
  
  </div>