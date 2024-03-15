<script>
  export let name;
  export let label;
  export let controlType;
  export let rows;
  export let value;
</script>

{#if controlType === "textarea"}
  <div class="form-control">
    <label for={name}>{label}</label>
    <textarea {rows} type="text" id="name" {value} on:input />
  </div>
{:else}
  <div class="form-control">
    <label for={name}>{label}</label>
    <input type="text" id={name} {value} on:input />
  </div>
{/if}

<style>
  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    border: none;
    border-bottom: 2px solid #ccc;
    border-radius: 3px 3px 0 0;
    background: white;
    padding: 0.15rem 0.25rem;
    transition: border-color 0.1s ease-out;
  }

  input:focus,
  textarea:focus {
    border-color: #e40763;
    outline: none;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    width: 100%;
  }

  .form-control {
    padding: 0.5rem 0;
    width: 100%;
    margin: 0.25rem 0;
  }
</style>
