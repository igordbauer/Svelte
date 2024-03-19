<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";

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
      isFavorite: false,
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
      isFavorite: false,
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
      isFavorite: false,
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
      isFavorite: false,
    },
  ];

  let editMode = null;

  let title = "";
  let subtitle = "";
  let description = "";
  let email = "";
  let address = "";
  let imageUrl = "";

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = { ...meetups.find((e) => e.id === id) };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex((e) => e.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }

  export const addMeetup = () => {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      contactEmail: email,
      address: address,
      imageUrl: imageUrl,
      isFavorite: false,
    };
    meetups = [newMeetup, ...meetups];
  };
</script>

<Header />
<main>
  <div class="button">
    <Button caption="Add Meetup" on:click={() => (editMode = "add")} />
  </div>
  {#if editMode === "add"}
    <EditMeetup />
  {/if}
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>

<style>
  .button {
    margin-top: 5rem;
  }
</style>
