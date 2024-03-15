<script>
  import MeetupItem from "../UI/meetupItem.svelte";
  export let meetups;
</script>

<section id="meetups">
  {#each meetups as meetup, index (meetup.id)}
    <MeetupItem
      title={meetup.title}
      subtitle={meetup.subtitle}
      description={meetup.description}
      imageUrl={meetup.imageUrl}
      address={meetup.address}
      contactEmail={meetup.contactEmail}
    />
  {/each}
</section>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  #meetups {
    margin-top: 5rem;
  }
</style>
