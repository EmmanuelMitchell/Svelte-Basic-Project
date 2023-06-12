<script>
import Footer from "./component/Footer.svelte";
import Header from "./component/Header.svelte";
import DetailsTabs from "./sharedtab/DetailsTabs.svelte";
import CreateForm from "./component/CreateForm.svelte";
  import PollList from "./component/PollList.svelte";

  
  let  DetailsItems = ["Current Items", "Add New Items"];
  let activeDetailsItems = "Current Items";


   
    function clickItems(e){
      activeDetailsItems = e.detail
    }

    //DataForthe Question
    let pollsData = [
        {  
         id: 1,
         Question: "Svelte and React Which one is more simpleer",
         Answera: "React",
         Answerb: "Svelte",
         voteA: 10,
         voteB: 5
        }
    ]

    function handlePoll(e){
        const pollData = e.detail;
         pollsData = [pollData, ...pollsData]
         console.log(pollsData)

         activeDetailsItems = "Current Items";
    }
</script>
<Header />    
<main class="max-w-[960px] mt-40 m-auto">
 <DetailsTabs {DetailsItems} {activeDetailsItems} on:clickItems={clickItems}/>
       {#if activeDetailsItems === "Current Items"}
       <PollList {pollsData} />
         <p>curren Pools</p>
         {:else if activeDetailsItems === "Add New Items"}
           <CreateForm on:addPoll={handlePoll}/>
         <p>New Pools</p>
       {/if}
</main>


<Footer />

<style>
 
</style>

