<script lang="js">
    import logo from "$public/logo-white.png"
    import {logout} from "../../hooks/auth"

    import {fetchUserData} from "../../hooks/handleUser"

    import { onMount } from "svelte";
    let user = '';

    onMount(async ()=>{
      user = await fetchUserData();
    })
</script>
   
<div class="flex w-[7%] justify-start">
    <div class="container absolute flex flex-col w-[7%] h-[100%] bg-main border-r-2 border-r-white ">

      <div class="flex flex-wrap justify-start px-2 py-4 items-center gap-x-4 mr-3.5">
        <img src={logo} alt="" class="w-14 h-14 ml-2"/>
        <h3 class="text absolute ml-20 font-bold text text-2xl text-white font-sans hidden">CORE1</h3>
      </div>      
      <hr class="text self-center border-t-2 border-accent w-[80%] opacity-0"> 

      <div class="btn_container flex flex-col w-[100%] h-[auto] gap-y-5 pt-10">

        <a class="unhover" href="/DashboardPage/staff/dashboard">
          <button class="btn ml-5 flex flex-wrap group hover:bg-accent text-base text-black items-center rounded-3xl w-[40%] h-10 px-4">
              <svg class="icon mt-1 flex absolute fill-mainParagraph w-5 h-5 mr-5 group-hover:fill-main" xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 576 512">
                <path d="M575.8 255.5c0 18-15 32.1-32 32.1h-32l.7 160.2c0 2.7-.2 5.4-.5 8.1V472c0 22.1-17.9 40-40 40H456c-1.1 0-2.2 0-3.3-.1c-1.4 .1-2.8 .1-4.2 .1H416 392c-22.1 0-40-17.9-40-40V448 384c0-17.7-14.3-32-32-32H256c-17.7 0-32 14.3-32 32v64 24c0 22.1-17.9 40-40 40H160 128.1c-1.5 0-3-.1-4.5-.2c-1.2 .1-2.4 .2-3.6 .2H104c-22.1 0-40-17.9-40-40V360c0-.9 0-1.9 .1-2.8V287.6H32c-18 0-32-14-32-32.1c0-9 3-17 10-24L266.4 8c7-7 15-8 22-8s15 2 21 7L564.8 231.5c8 7 12 15 11 24z"/>
              </svg>
              <p class="text text-mainParagraph self-center hidden group-hover:text-main ">Dashboard</p>
          </button>
        </a>  

        <a class="unhover" href="/DashboardPage/staff/appointments">
            <button class="btn ml-5 flex flex-wrap group hover:bg-accent text-base text-black items-center rounded-3xl w-[40%] h-10 px-4">
                <svg class="icon mt-1 flex absolute fill-mainParagraph w-5 h-5 mr-5 group-hover:fill-main" xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 576 512">
                  <path d="M575.8 255.5c0 18-15 32.1-32 32.1h-32l.7 160.2c0 2.7-.2 5.4-.5 8.1V472c0 22.1-17.9 40-40 40H456c-1.1 0-2.2 0-3.3-.1c-1.4 .1-2.8 .1-4.2 .1H416 392c-22.1 0-40-17.9-40-40V448 384c0-17.7-14.3-32-32-32H256c-17.7 0-32 14.3-32 32v64 24c0 22.1-17.9 40-40 40H160 128.1c-1.5 0-3-.1-4.5-.2c-1.2 .1-2.4 .2-3.6 .2H104c-22.1 0-40-17.9-40-40V360c0-.9 0-1.9 .1-2.8V287.6H32c-18 0-32-14-32-32.1c0-9 3-17 10-24L266.4 8c7-7 15-8 22-8s15 2 21 7L564.8 231.5c8 7 12 15 11 24z"/>
                </svg>
                <p class="text text-mainParagraph self-center hidden group-hover:text-main ">Appointments</p>
            </button>
          </a>  

          <a class="unhover" href="/DashboardPage/staff/logs">
            <button class="btn ml-5 flex flex-wrap group hover:bg-accent text-base text-black items-center rounded-3xl w-[40%] h-10 px-4">
                <svg class="icon mt-1 flex absolute fill-mainParagraph w-5 h-5 mr-5 group-hover:fill-main" xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 576 512">
                  <path d="M575.8 255.5c0 18-15 32.1-32 32.1h-32l.7 160.2c0 2.7-.2 5.4-.5 8.1V472c0 22.1-17.9 40-40 40H456c-1.1 0-2.2 0-3.3-.1c-1.4 .1-2.8 .1-4.2 .1H416 392c-22.1 0-40-17.9-40-40V448 384c0-17.7-14.3-32-32-32H256c-17.7 0-32 14.3-32 32v64 24c0 22.1-17.9 40-40 40H160 128.1c-1.5 0-3-.1-4.5-.2c-1.2 .1-2.4 .2-3.6 .2H104c-22.1 0-40-17.9-40-40V360c0-.9 0-1.9 .1-2.8V287.6H32c-18 0-32-14-32-32.1c0-9 3-17 10-24L266.4 8c7-7 15-8 22-8s15 2 21 7L564.8 231.5c8 7 12 15 11 24z"/>
                </svg>
                <p class="text text-mainParagraph self-center hidden group-hover:text-main ">Logs</p>
            </button>
          </a>

          <a class="unhover" href="/DashboardPage/staff/profile">
            <button class="btn ml-5 flex flex-wrap group hover:bg-accent text-base text-black items-center rounded-3xl w-[40%] h-10 px-4">
                <svg class="icon mt-1 flex absolute fill-mainParagraph w-5 h-5 mr-5 group-hover:fill-main" xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 576 512">
                  <path d="M575.8 255.5c0 18-15 32.1-32 32.1h-32l.7 160.2c0 2.7-.2 5.4-.5 8.1V472c0 22.1-17.9 40-40 40H456c-1.1 0-2.2 0-3.3-.1c-1.4 .1-2.8 .1-4.2 .1H416 392c-22.1 0-40-17.9-40-40V448 384c0-17.7-14.3-32-32-32H256c-17.7 0-32 14.3-32 32v64 24c0 22.1-17.9 40-40 40H160 128.1c-1.5 0-3-.1-4.5-.2c-1.2 .1-2.4 .2-3.6 .2H104c-22.1 0-40-17.9-40-40V360c0-.9 0-1.9 .1-2.8V287.6H32c-18 0-32-14-32-32.1c0-9 3-17 10-24L266.4 8c7-7 15-8 22-8s15 2 21 7L564.8 231.5c8 7 12 15 11 24z"/>
                </svg>
                <p class="text text-mainParagraph self-center hidden group-hover:text-main ">Profile</p>
            </button>
          </a>  

          <div class="w-[90%]"> 
            <button on:click={logout} class="btn ml-5 flex flex-wrap group hover:bg-accent text-base text-black items-center gap-x-5 rounded-3xl w-[40%] h-10 px-4">
              <svg class="unhover icon mt-1 flex absolute fill-mainParagraph w-5 h-5 mr-5 group-hover:fill-main" xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 512 512"><path d="M377.9 105.9L500.7 228.7c7.2 7.2 11.3 17.1 11.3 27.3s-4.1 20.1-11.3 27.3L377.9 406.1c-6.4 6.4-15 9.9-24 9.9c-18.7 0-33.9-15.2-33.9-33.9l0-62.1-128 0c-17.7 0-32-14.3-32-32l0-64c0-17.7 14.3-32 32-32l128 0 0-62.1c0-18.7 15.2-33.9 33.9-33.9c9 0 17.6 3.6 24 9.9zM160 96L96 96c-17.7 0-32 14.3-32 32l0 256c0 17.7 14.3 32 32 32l64 0c17.7 0 32 14.3 32 32s-14.3 32-32 32l-64 0c-53 0-96-43-96-96L0 128C0 75 43 32 96 32l64 0c17.7 0 32 14.3 32 32s-14.3 32-32 32z"/>
              </svg>
              <p class="text text-mainParagraph self-center hidden group-hover:text-main">Logout</p>
            </button>
          </div>
       


      </div>

      <div class="account relative flex flex-col  items-center justify-end h-[100%] opacity-0 my-4">
        
  
            <div class="self-center justify-self-center mb-1">
              <strong class="text-sm text-mainParagraph">{user.full_name}</strong>
            </div>     
            
            <div class="self-center">
              <p class="text-xs text-mainParagraph">{user.email}@gmail.com</p>
            </div>        
          </div>
      


    </div>
  </div> 
   
<style>
   
  .container{
    transition: width 1s;
  }

  @keyframes fadeIn {
    0% {
      opacity: 0; /* Start with opacity 0 */
      
    }

    20% {
      opacity: 0; /* Start with opacity 0 */
      
    }

    50% {
      opacity: .4; /* Start with opacity 0 */
      
    }

    80% {
      opacity: .8 ; /* Start with opacity 0 */
      
    }

    100% {
      opacity: 1; /* End with opacity 100% (fully visible) */
    }
  }

  .container:hover{ 
    width: 16%;
    position: absolute;
  }

  

  .container:hover .btn, a{
    display: block;
    width: 90%;
    
  }
/* 
  .container:hover .icon{
  fill: #F9BC60;
  }
*/

  .container:hover .text{
    display: block;
    animation: fadeIn 1s linear forwards;
  }

  .container:hover .account{
    animation: fadeIn 1s linear forwards;
  }

  .btn:focus .icon{
  fill: #f9bc60;
  }
  
</style>