<script>
  import {fetchNonPendingAppointments} from '../../hooks/handleBook';

  import { onMount } from "svelte";
  import { format } from 'date-fns';
  import { paginate, LightPaginationNav } from 'svelte-paginate'
  import LogsData from './LogsData.svelte';
  


  let books = [];

  $: items = books;
  let currentPage = 1
  let pageSize = 8;
  let paginatedItems = [];

  $: updatePaginatedItems = () => {
    paginatedItems = paginate({ items, pageSize, currentPage });
  };

  $: {
    updatePaginatedItems();
  }

  onMount(async() =>{
    books = await fetchNonPendingAppointments();

    console.log(books)
    books.forEach(e => {
      let dateString = e.book_date;
      let parsedDate = new Date(dateString);
      const formattedDate = format(parsedDate, 'MMMM d, yyyy');
      e.book_date = formattedDate;
      
    });

    updatePaginatedItems();
    
  })

  let showModal = false;

  const viewRemark = async () =>{
      showModal = true;
  }

</script>

<div class="flex flex-col w-[93%] justify-start items-center"> 
  <div class="flex flex-col justify-start items-start w-[80%] my-4">
   
    <div class="text-2xl font-bold text-main">Logs</div> 
  </div>
  
  <div class="flex flex-row justify-center items-start w-[80%] my-4">
   
    <div class="text-xl font-semibold text-main">Appointments</div> 
  </div>


  <!--LOGS TABLE-->
  <div class="flex items-center justify-center min-h-[450px] w-[80%] mb-4">
  
    <div class="flex flex-col justify-between overflow-x-auto overflow-y-auto  shadow-md rounded-sm w-[100%] h-[79vh] mt-2">
  
      <table class="min-w-full text-sm text-left text-primary">
        
        <thead class="text-xs text-white uppercase  bg-main ">
        
          <tr>
            <th scope="col" class="py-3 px-6">BOOK ID</th>
            <th scope="col" class="py-3 px-6">USER</th>
            <th scope="col" class="py-3 px-6">BOOKING DATE </th>
            <th scope="col" class="py-3 px-6">PHONE MODEL</th>
            <th scope="col" class="py-3 px-6">ISSUE DESCRIPTION</th>
            <th scope="col" class="py-3 px-6 overflow-y-auto">APPOINTMENT STATUS</th>
            <th scope="col" class="py-3 px-6"></th>
          </tr>
        </thead>

        <tbody>
          {#each paginatedItems as book}
            <LogsData
              book_id = {book.book_id }
              user_id = {book.user_id }
              book_date = {book.book_date }
              cellphone_model = {book.cellphone_model }
              issue_description = {book.issue_description }
              appointment_status = {book.appointment_status }
              remark = {book.remark }
            />

            
           

            
          {/each}
        </tbody>

      </table>
      
      <LightPaginationNav
        totalItems="{items.length}"
        pageSize="{pageSize}"
        currentPage="{currentPage}"
        limit="{1}"
        showStepOptions="{true}"
        on:setPage="{(e) => currentPage = e.detail.page}"
      />
    </div>

  </div>


</div>

