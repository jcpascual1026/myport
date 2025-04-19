<script lang="ts">
  import { fly } from 'svelte/transition';
  import { cubicOut } from 'svelte/easing';
  import login from '$lib/images/Log-in.png';
  import logo from '$lib/Images/Octa.png';

  let studentNumber = '';
  let studentName = 'JC Pascual';
  let studentSection = 'BSCS-1A'; 
  let showLogin = false;

  function submitStudentNumber() {
    if (studentNumber) {
      console.log("Student number submitted:", studentNumber);
      showLogin = true;
    }
  }

  function goBack() {
    showLogin = false;
  }
</script>

<div class="flex text-black w-full">
  <div class="w-1/2 mx-auto" id="Login">
    <div class="flex items-center m-2">
      <img alt="" src={logo} class="h-12 w-auto" />
      <h1 class="ml-1 p-3 font-bold tracking-widest text-2xl">OCTA</h1>
    </div>
    <div class="transition-wrapper">
      {#if !showLogin}
        <div class="form-content" transition:fly="{{ y: 100, duration: 900, easing: cubicOut }}">
          <div class="flex flex-col justify-center w-full mx-auto">
            <div class="text-center my-20">
              <h1 class="text-6xl font-bold my-2">Welcome</h1>
              <p class="text-shad">Please enter your student number</p>
            </div>
            <form on:submit|preventDefault={submitStudentNumber} class="w-full max-w-md mx-auto text-center">
              <label for="studentNumber" class="block text-sm font-bold mb-2 ml-[-7rem] w-full">Student Number</label>
              <input type="text" id="studentNumber" bind:value={studentNumber} placeholder="Ex. 0324-0000" required class="border px-2 py-2 w-3/4 rounded mb-14 text-shad hover:text-black"maxlength="9"/>
              <input type="submit" value="Verify" class="bg-yellowish text-white px-4 py-2 rounded-lg hover:bg-yellow-500 w-3/4 shadow-xl buttonh"disabled={!studentNumber}/>
            </form>
          </div>
        </div>
      {/if}

      {#if showLogin}
        <div class="form-content" transition:fly="{{ y: -100, duration: 900, easing: cubicOut }}">
          <div class="flex flex-col w-full mx-auto">
            <div class="text-center mt-10">
              <h1 class="text-6xl font-bold my-4">Verify it’s you</h1>
            </div>
            <form class="flex flex-col items-center mt-6 w-full max-w-md mx-auto" on:submit|preventDefault={() => {}}>
              <div class="w-full mb-6">
                <label for="StudentName" class="block text-left text-sm font-bold mb-2">Name</label>
                <input type="text" id="StudentName" value={studentName} readonly class="border border-gray-300 rounded px-3 py-2 w-full text-sm bg-gray-100"/>
                <label for="StudentSection" class="block text-left text-sm font-bold mt-4 mb-2">Section</label>
                <input type="text" id="StudentSection" value={studentSection} readonly class="border border-gray-300 rounded px-3 py-2 w-full text-sm bg-gray-100"/>
              </div>
              <input type="submit" value="Continue"class="bg-yellowish text-white text-sm px-4 py-2 rounded-md hover:bg-yellow-500 w-full shadow-xl buttonh"/>
            </form>
            <button class="text-sm text-center font-bold mt-12 text-black cursor-pointer hover:underline" on:click={goBack}>
              Go back to login page 
            </button>
          </div>
        </div>
      {/if}
    </div>
  </div>

  <div class="w-[80vh] h-[100vh]">
    <img src={login} alt="Login Visual" class="w-full h-full m-0 object-center object-fill"/>
  </div>
</div>
