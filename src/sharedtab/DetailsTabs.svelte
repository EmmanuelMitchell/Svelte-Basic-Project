<script>
import { createEventDispatcher } from "svelte";

const dispatch = createEventDispatcher()

export let DetailsItems;
export let activeDetailsItems;
</script>


<main>
  <ul class="flex justify-center gap-2 items-center mb-6">
    {#each DetailsItems as item }
    <li class="cursor-wait text-gray-700 mt-0 ml-2" on:click={()=> dispatch("clickItems", item)}>
        <div class:active={activeDetailsItems === item}>{item}</div>
    </li>
        
    {/each}
  </ul>
</main>


<style>
  .active{
    color: #a52a2a;
    border-bottom: 2px solid #a52a2a;
  }
</style>