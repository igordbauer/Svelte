<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Max";
  let title = "";
  let image = "";
  let description = "";
  let formState = "empty";
  let createdContacts = [];

  const deleteContact = (id) => {
    createdContacts = createdContacts.filter((e) => e.id !== id);
  };

  const addContact = () => {
    if (
      name.trim().length == 0 ||
      title.trim().length == 0 ||
      description.trim().length == 0 ||
      image.trim().length == 0
    ) {
      formState = "invalid";
      return;
    }
    createdContacts = [
      ...createdContacts,
      {
        id: Math.random(),
        name,
        jobTitle: title,
        imageUrl: image,
        description,
      },
    ];
    formState = "done";
  };
</script>

<!-- https://ufsb.edu.br/cfsaude/images/galeria_em_artigos/image03_grd.png -->

<form id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
  <!-- event modifier => preventDefault -->
  <button on:click|preventDefault={addContact} type="submit"
    >Add Contact Card</button
  >
</form>

{#if formState === "invalid"}
  <p>Invalid Input!</p>
{:else if formState === "empty"}
  <p>Please enter some data and hit the button!</p>
{:else}
  {#each createdContacts as contact, i (contact.id)}
    <h2>#{i}</h2>
    <ContactCard
      userName={contact.name}
      jobTitle={contact.jobTitle}
      description={contact.description}
      userImage={contact.image}
    />
    <button on:click={() => deleteContact(contact.id)}>Delete</button>
  {:else}
    <p>Please insert some contact!</p>
  {/each}
{/if}

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>
