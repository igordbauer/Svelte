<script>
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import { createEventDispatcher } from "svelte";

  let title = "";
  let subtitle = "";
  let description = "";
  let email = "";
  let address = "";
  let imageUrl = "";

  const dispatch = createEventDispatcher();

  const submitForm = () => {
    dispatch("save", {
      title: title,
      subtitle: subtitle,
      address: address,
      email: email,
      description: description,
      imageUrl: imageUrl,
    });
  };
</script>

<form on:submit|preventDefault={submitForm}>
  <TextInput
    name="title"
    label="Title"
    value={title}
    on:input={(e) => (title = e.target.value)}
  />
  <TextInput
    name="subtitle"
    label="Subtitle"
    value={subtitle}
    on:input={(e) => (subtitle = e.target.value)}
  />
  <TextInput
    name="address"
    label="Address"
    value={address}
    on:input={(e) => (address = e.target.value)}
  />
  <TextInput
    name="email"
    label="E-mail"
    value={email}
    on:input={(e) => (email = e.target.value)}
  />
  <TextInput
    name="imageUrl"
    label="Image URL"
    value={imageUrl}
    on:input={(e) => (email = e.target.value)}
  />
  <TextInput
    name="description"
    label="Description"
    value={description}
    controlType="textarea"
    rows="3"
    on:input={(e) => (description = e.target.value)}
  />
  <Button type="submit" caption="Save" />
</form>

<style>
  form {
    margin: auto;
    margin-top: 5rem;
    width: 30rem;
    max-width: 90%;
  }
</style>
