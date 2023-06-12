<script>
  import PollDetails from "./PollDetails.svelte";

  export let pollsData = [];
</script>


<main>
  {#each pollsData as poll (poll.id) }
    <PollDetails {poll} />
  {/each}
</main>


<style>

</style>