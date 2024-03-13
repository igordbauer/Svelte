<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Igor";
  let jobTitle = "Um belo titulo";
  let description = "uma bela descrição";
  let imageUrl =
    "https://ufsb.edu.br/cfsaude/images/galeria_em_artigos/image03_grd.png";

  $: uppercaseName = name.toUpperCase();

  $: console.log(name);
  $: if ((name = "Igor")) {
  }
</script>

<h1>Hello my name is {uppercaseName}, i have years old!</h1>
<!-- <button on:click={changeAge}>Change age!</button> -->
<!-- <button on:click={changeName}>Change name!</button> -->

<input type="text" bind:value={name} />
<input type="text" bind:value={jobTitle} />
<input type="text" bind:value={imageUrl} />
<input type="text" bind:value={description} />
<ContactCard {...{ name, jobTitle, description, imageUrl }} />

<style>
  h1 {
    color: purple;
  }
</style>
