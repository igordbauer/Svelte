<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  let meetups = [
    {
      id: "m0",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup will have som experts that teach you to how to code better!",
      imageUrl:
        "https://addicted2success.com/wp-content/uploads/2018/06/8-Reasons-You-Should-Join-a-Meetup-Group-Today.jpg",
      address: "27th Nerd Road, 32523 new Yourk",
      contactEmail: "code@test.com",
    },
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup will have som experts that teach you to how to code better!",
      imageUrl:
        "https://addicted2success.com/wp-content/uploads/2018/06/8-Reasons-You-Should-Join-a-Meetup-Group-Today.jpg",
      address: "27th Nerd Road, 32523 new Yourk",
      contactEmail: "code@test.com",
    },
    {
      id: "m2",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup will have som experts that teach you to how to code better!",
      imageUrl:
        "https://addicted2success.com/wp-content/uploads/2018/06/8-Reasons-You-Should-Join-a-Meetup-Group-Today.jpg",
      address: "27th Nerd Road, 32523 new Yourk",
      contactEmail: "code@test.com",
    },
    {
      id: "m3",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup will have som experts that teach you to how to code better!",
      imageUrl:
        "https://addicted2success.com/wp-content/uploads/2018/06/8-Reasons-You-Should-Join-a-Meetup-Group-Today.jpg",
      address: "27th Nerd Road, 32523 new Yourk",
      contactEmail: "code@test.com",
    },
  ];

  let title = "";
  let subtitle = "";
  let description = "";
  let email = "";
  let address = "";
  let imageUrl = "";

  const addMeetup = () => {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      contactEmail: email,
      address: address,
      imageUrl: imageUrl,
    };
    console.log(newMeetup);
    meetups = [newMeetup, ...meetups];
  };
</script>

<Header />
<main>
  <form on:submit|preventDefault={addMeetup}>
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
  <MeetupGrid {meetups} />
</main>

<style>
  form {
    margin: auto;
    margin-top: 5rem;
    width: 30rem;
    max-width: 90%;
  }
</style>
