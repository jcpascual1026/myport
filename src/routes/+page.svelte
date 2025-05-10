<script lang="ts">
  import { fly } from 'svelte/transition';
  import { cubicOut } from 'svelte/easing';
  import login from '$lib/images/Log-in.png';
  import Octa from '$lib/Images/Octa.png';
  import Algo from '$lib/images/Algo.png';
  import BSIT from '$lib/Images/BSIT.png';

  let studentNumber = '';
  let studentName = 'JC Pascual';
  let studentSection = 'BSCS-1A';
  let showLogin = false;
  let showCredits = false;

  function submitStudentNumber() {
    if (studentNumber) {
      console.log("Student number submitted:", studentNumber);
      showLogin = true;
    }
  }

  function goBack() {
    showLogin = false;
  }

  function toggleCredits() {
    showCredits = !showCredits;
  }
</script>

<!-- Main container -->
<div class="flex flex-col lg:flex-row flex-wrap text-black w-full">

  <!-- SVG Button -->
  <!-- svelte-ignore a11y_consider_explicit_label -->
  <button class="flex flex-col justify-end w-5 h-[95vh] m-4 cursor-pointer" on:click={toggleCredits}>
    <svg fill="#000000" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" 
         xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 416.979 416.979" xml:space="preserve">
      <g><path d="M356.004,61.156c-81.37-81.47-213.377-81.551-294.848-0.182
        c-81.47,81.371-81.552,213.379-0.181,294.85
        c81.369,81.47,213.378,81.551,294.849,0.181
        C437.293,274.636,437.375,142.626,356.004,61.156z
        M237.6,340.786c0,3.217-2.607,5.822-5.822,5.822h-46.576
        c-3.215,0-5.822-2.605-5.822-5.822V167.885
        c0-3.217,2.607-5.822,5.822-5.822h46.576
        c3.215,0,5.822,2.604,5.822,5.822V340.786z
        M208.49,137.901c-18.618,0-33.766-15.146-33.766-33.765
        c0-18.617,15.147-33.766,33.766-33.766
        c18.619,0,33.766,15.148,33.766,33.766
        C242.256,122.755,227.107,137.901,208.49,137.901z"></path></g>
    </svg>
  </button>

  <!-- Credits Modal -->
  {#if showCredits}
    <div class="absolute inset-0 bg-black/30 backdrop-blur-sm flex justify-center items-center z-50"
         transition:fly={{ y: 20, duration: 500 }}>
      <div class="p-6 bg-white text-black rounded-xl shadow-lg backdrop-blur-md w-[90%] max-w-xl">
        <div class="flex justify-between">
          <h2 class="text-2xl font-bold mb-3 mr-2">Developers Credits</h2>
          <!-- svelte-ignore a11y_consider_explicit_label -->
          <button on:click={toggleCredits}>
            <div class="w-7 h-auto pb-2.5 cursor-pointer">
              <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" clip-rule="evenodd"
                      d="M5.29289 5.29289C5.68342 4.90237 6.31658 4.90237 6.70711 5.29289L12 10.5858
                      L17.2929 5.29289C17.6834 4.90237 18.3166 4.90237 18.7071 5.29289C19.0976 5.68342
                      19.0976 6.31658 18.7071 6.70711L13.4142 12L18.7071 17.2929C19.0976 17.6834
                      19.0976 18.3166 18.7071 18.7071C18.3166 19.0976 17.6834 19.0976 17.2929 18.7071
                      L12 13.4142L6.70711 18.7071C6.31658 19.0976 5.68342 19.0976 5.29289 18.7071
                      C4.90237 18.3166 4.90237 17.6834 5.29289 17.2929L10.5858 12
                      L5.29289 6.70711C4.90237 6.31658 4.90237 5.68342 5.29289 5.29289Z"
                      fill="#0F1729"/>
              </svg>
            </div>
          </button>
        </div>

        <div class="my-5 list-disc">
          <h2 class="text-xl font-bold mb-3 mr-2">Project Leadership</h2>
          <ul>
            <li>Natividad, John Marky A. <span>- Director, Backend</span></li>
            <li>Fernandez, Patrick Joel P. <span>- Associate Director, Backend</span></li>
            <li>Furaque, John Patrick F. <span>- Quality Assurance</span></li>
            <li>Comia, Joko Ymmanuel A. <span>- Design Team Leader</span></li>
            <li>Dollentes, Mark Daniel B. <span>- Frontend Team Leader</span></li>
          </ul>
        </div>

        <div class="list-disc">
          <h2 class="text-xl font-bold mb-3 mr-2">Development Team</h2>
          <ul>
            <li>Bartolome, Joshua L. <span>- Frontend Developer</span></li>
            <li>Briones, Gio Andrew T. <span>- Designer</span></li>
            <li>Janolino, Justine S. <span>- Designer</span></li>
            <li>Pascual, John Christopher A. <span>- Frontend Developer</span></li>
          </ul>
        </div>
      </div>
    </div>
  {/if}

  <div class="w-full lg:w-1/2 px-4 mx-auto" id="Login">
    <div class="flex flex-wrap items-center m-4 justify-center">
      <img alt="" src={Algo} class="h-auto w-10 pt-6" />
      <h1 class="ml-1 p-3 font-bold tracking-[0.2em] text-2xl mt-6">ALGO</h1>
      <img alt="" src={Octa} class="h-12 w-auto" />
      <h1 class="ml-1 p-3 font-bold tracking-[0.2em] text-2xl">OCTA</h1>
      <img alt="" src={BSIT} class="h-auto w-10 pt-6" />
      <h1 class="ml-1 p-3 font-bold tracking-[0.2em] text-2xl mt-6">BSIT</h1>
    </div>

    <div class="transition-wrapper">
      {#if !showLogin}
        <div class="form-content" transition:fly="{{ y: 100, duration: 900, easing: cubicOut }}">
          <div class="flex flex-col justify-center w-full mx-auto">
            <div class="text-center mt-20 mb-10">
              <h1 class="text-6xl font-bold my-2">Welcome</h1>
              <p class="text-shad w-4/5 md:w-3/5 m-auto">
                This website is the official elections portal for the Organization for Computing and Technological Advancement (OCTA).
              </p>
            </div>
            <form on:submit|preventDefault={submitStudentNumber}
                  class="w-full max-w-md mx-auto flex flex-col items-center text-center">
              <label for="studentNumber" class="block text-sm font-bold mb-2 w-full text-left">Student Number</label>
              <input type="text" id="studentNumber" bind:value={studentNumber} placeholder="Please enter your student number" required class="border px-3 py-2 w-full rounded mb-6 text-shad hover:text-black" maxlength="9"/>
              <input type="submit" value="Verify" class="bg-yellowish text-white px-4 py-2 rounded-lg hover:bg-yellow-500 w-full shadow-xl buttonh cursor-pointer mt-5" disabled={!studentNumber}/>
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
              <input type="submit" value="Continue" class="bg-yellowish text-white text-sm px-4 py-2 rounded-md hover:bg-yellow-500 w-full shadow-xl buttonh"/>
            </form>
            <button class="text-sm text-center font-bold mt-12 text-black cursor-pointer hover:underline" on:click={goBack}>
              Go back to login page 
            </button>
          </div>
        </div>
      {/if}
    </div>

    <div class="text-sm w-full max-w-prose mx-auto text-gray-400 px-4 sm:px-6 md:px-8">
      <!-- svelte-ignore a11y_invalid_attribute -->
      <p class="text-center">
      We value your feedback and concerns. If you have any, please don't hesitate to contact us via this 
      <a href="#" class="text-blue-300 decoration-solid">email</a>.
      </p>
    </div>
</div>


  <div class="hidden lg:block w-full lg:w-[40%] h-[50vh] lg:h-[100vh]">
    <img src={login} alt="Login Visual" class="w-full h-full m-0 object-center object-fill"/>
  </div>

</div>
