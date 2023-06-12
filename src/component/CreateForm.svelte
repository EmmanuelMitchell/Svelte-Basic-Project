<script>
import { createEventDispatcher } from "svelte";
import Button from "../sharedtab/Button.svelte";

const dispatch = createEventDispatcher()


let formFields = {
    Question: "",
     Answera: "",
     Answerb: ""
     
     }

let errors = {
    Question: "",
     Answera: "",
     Answerb: ""
     
     }

let valid = false;



     function handleSubmite(){
        valid = true
        // Validation for the Question 
        if(formFields.Question.trim().length < 5){
            valid = false
            errors.Question = "this need to be at least 5 character Longs"
        }else{
            errors.Question = ""
        }


        // Validation for AnswerA
        if(errors.Answera.trim().length < 1){
            valid = false;
            errors.Answera = "Answer A Character must be mor than one"
        }else{
            errors.Answera = ""
        }


        //Validation for AnserB

        if(errors.Answerb.trim().length < 1){
            valid = false;
            errors.Answerb = "Answer A Character must be mor than one"
        }else{
            errors.Answerb = ""
        }

        if(valid){
            let pollData = {...formFields, voteA: 0, voteB: 0, id: Math.random()}
            dispatch("addPoll", pollData)
            // console.log("valide",formFields)
        }
     
     }
</script>


<main>
    <!-- <div class="w-full mx-auto max-w-xs shadow-xl bg-slate-50"> -->
        <form on:submit|preventDefault={handleSubmite}  class="bg-white  rounded px-8 pt-6 pb-8 mb-4">
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="Question">
              Svelte Question
            </label>
            <input bind:value={formFields.Question} class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="Question" type="text">
            <p class="text-red-600 font-bold">{errors.Question}</p>
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="Answer-A">
              Answer A
            </label>
            <input bind:value={formFields.Answera} class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="Answer-A" />
            <p class="text-red-600 font-bold">{errors.Answera}</p>
          </div>


          <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="Answer-B">
              Answer B
            </label>
            <input bind:value={formFields.Answerb} class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="Answer-B" />
            <p class="text-red-600 font-bold">{errors.Answerb}</p>
          </div>
          <div >
          <Button  btnType="secondary" flat={true} invase={true}>Add</Button>
          </div>
        </form>

      <!-- </div> -->

</main>


<style>

</style>