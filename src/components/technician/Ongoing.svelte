<script>
  import { onMount } from "svelte";
  import OngoingRepairs from "./OngoingRepairs.svelte";
  import { format } from 'date-fns';
  import {fetchRepairingBook} from "../../hooks/handleBook"

  let repairingBooks = [];

  onMount(async() =>{
    repairingBooks = await fetchRepairingBook();
    repairingBooks.forEach(e => {
        let dateString = e.book_date;
        let parsedDate = new Date(dateString);
        const formattedDate = format(parsedDate, 'MMMM d, yyyy');
        e.book_date = formattedDate;
        
      });
    console.log(repairingBooks)
    
    
  })
</script> 


<div class="flex flex-col justify-start items-center w-[93%]  ">
  <div class="flex flex-col justify-start items-start w-[80%] my-4  gap-2 ">
    <div class="text-2xl font-bold text-main">Ongoing Repairs</div>
  </div>

  <div class="flex flex-col justify-start items-start w-[80%] my-4 gap-2">

    {#if repairingBooks.length == 0}
      <div class="text-lg font-semibold text-main">No Ongoing Repairs Yet...</div> 

    {:else}
      {#each repairingBooks as repairingBook}
      <OngoingRepairs
    
    
        book_date = {repairingBook.book_date}
        book_id = {repairingBook.book_id}
        cellphone_model = {repairingBook.cellphone_model}
        issue_description = {repairingBook.issue_description}
        username = {repairingBook.username}
        />
      {/each}
    {/if}

  
  
  </div>
</div>







<style>


</style>