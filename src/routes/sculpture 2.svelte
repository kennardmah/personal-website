<script lang="ts">
  import ChevronDown from "$lib/icon/heroicons/ChevronDown.js";
  import Icon from "$lib/icon/Icon.svelte";
  import Menu from "$lib/menu/Menu.svelte";
  import MenuIcon from "$lib/menu/MenuIcon.svelte";
  import { OnMount } from "fractils";
  import { fly, fade } from "svelte/transition";

  import Plus from '$lib/icon/heroicons/Plus.js';

  import InformationCircle from '$lib/icon/heroicons/InformationCircle.js';

  import Images from "$lib/sections/white-city/wcs-images.svelte";
 
  import { OnMount } from "fractils";
  import { fly, fade } from "svelte/transition";
  import { spring } from "svelte/motion";

  let manifesto = spring(0, {
    stiffness: 0.005,
    damping: 0.1,
  });

  let manifesto_open = false;

  $: {
    if (manifesto_open) manifesto.set(100);
    else manifesto.set(0);
  }

  let menuOpen = false;

  let closeMenu = () => (menuOpen = false);

  let node = '';
  
</script>

<head>
  <title> Dreamteam - White City Sculpture Challenge </title>
</head>

<div class="w-full h-0 fixed inset-0 flex flex-col justify-between z-50">
  <div
    class="flex items-center justify-between bg-black bg-opacity-75 backdrop-blur-xl p-2.5 md:p-5"
  >
    <a href="/" sveltekit:prefetch>
      <img src="/dreamteam.svg" alt="dreamteam" width="200" />
    </a>
    <button
      on:click={() => {
        menuOpen = !menuOpen;
      }}
      class="p-2"
    >
      <MenuIcon
        bind:open={menuOpen}
        class="w-6 xl:w-8 {menuOpen &&
          '-rotate-90'} transition-transform duration-300"
        fill="#fff"
      />
    </button>
  </div>
</div>

<Menu open={menuOpen} {closeMenu} />


<div class="w-full h-80 bg-black flex justify-center">
  <div class="relative w-full max-w-[1500px] overflow-hidden h-full mx-20">

    <video class= "w-100% h-auto% opacity-60"  allowfullscreen autoplay muted loop>
      <source src="static/projects/sculpture/Sculpture Challenge Draft 03.mov" type="video/mp4">
    </video>

    <div class="absolute top-20 p-8  flex justify-center min-w-[1500px] ">

      <!-- <div class="absolute inset-0 p-8 text-2xl">
        <p>WHITE CITY</p>
      </div>

      <div class="absolute top-30 left-1/4 p-20 text-center font-bold text-4xl">
        <p>SCULPTURE CHALLENGE</p>
      </div>

      <div class="absolute inset-[80px] p-8 text-xl font-thin">
        <p>2022</p>
      </div> -->
      <img src="static/projects/sculpture/Group 29.png" class=" w-[300px]" alt="nodes">

    </div>

  </div>
</div>



<!-- <div class="w-full h-56 bg-black flex overflow-hidden justify-center">
  <video class= "relative w-full max-w-full h-full bg-orange mx-20"  allowfullscreen autoplay muted loop>
        <source src="static/projects/sculpture/Sculpture Challenge Draft 03.mov" type="video/mp4">
    <div class="absolute inset-0 p-8 z-5 ">
      <h1>Test</h1>
    </div>
  </video>
</div> -->

<!-- 

<div
  class="relative w-full h-screen flex flex-col xl:flex-row xl:space-x-16 items-center justify-center p-8 xl:p-16">
   -->
    

  <!-- <div class="container relative flex overflow-hidden w-100% h-80 z-0 bg-transparent p-4 pt-30"> -->


    <!-- <div class="flex space-x-4">
      <Icon src={InformationCircle} solid width="20" />
      <h2>Click on a node to find out more</h2>
    </div> -->
    <!-- <div class="absolute flex justify-center items-center w-100% h-100% z-0 bg-transparent pl-60 p-2">
      <video class= "w-100% h-auto% opacity-60"  allowfullscreen autoplay muted loop>
        <source src="static/projects/sculpture/Sculpture Challenge Draft 03.mov" type="video/mp4">
      </video>

      <div class="absolute top-20 left-20 z-0 h-100% min-w-[850px] w-100% pl-20 pt-2">

        <div class="absolute flex justify-center z-40 text-white text-4xl pl-20 pt-11 font-bold  w-full text-5xl">
          <p>SCULPTURE CHALLENGE</p>
        </div>

        <div class="absolute z-40 text-white text-4xl pl-20 left-40 pt-2">
          <p>WHITE CITY</p>
        </div>

        <div class="absolute flex justify-end z-40 text-white text-4xl pt-20 right-20 font-thin">
          <p>2022</p>
        </div>
      </div>
    </div>  -->
          

      <!-- svelte-ignore a11y-media-has-caption -->
 
   
    
  <!-- </div> -->
  <!-- <div class="absolute z-5 text-white">
    <p>WHITE CITY SCULPTURE CHALLENGE</p>
  </div> -->

  <section class="w-100% flex flex-col justify-center p-4 space-y-12 xl:space-y-0 transition-all" id="what-we-do">
 
    <div
      class="w-100% flex flex-col items-center justify-center text-center space-y-8">
      <div class="flex flex-col space-y-4 items-center">
      

        <div class="flex space-x-4">
          <Icon src={InformationCircle} solid width="20" />
          <h2>Click on a node to find out more</h2>
        </div>
      </div>

      <div class="relative h-[150px] max-w-[650px] w-full">
        {#if node === 'brief'}
          <div transition:fade class="absolute top-0 flex flex-col space-y-5">
            <h2 class="text-lg">Brief</h2>
            <p>
              A Dreamteam iniative, The Sculpture Challenge was Imperial's first 
              student-led installation competition, driving synergy between art and science. 
              Student’s were tasked with creating an original work which will become 
              a permanent installation on the White City Campus. 
            </p>
          </div>
        {/if}

        {#if node === 'discover'}
          <div transition:fade class="absolute top-0 flex flex-col space-y-5">
            <h2 class="text-lg">Discover</h2>
            <p>
            Competitors were given collaborative opportunity to work in teams and create artwork 
            that communicates their definition of Imperial College culture. Student led design groups
            encouraged the development of creative talent in the Imperial environment and allowed STEM 
            students to apply their technical knowledge to support ideated concepts, driving synergy between art and science.
            </p>
          </div>
        {/if}

        {#if node === 'ideation'}
          <div transition:fade class="absolute top-0 flex flex-col space-y-5">
            <h2 class="text-lg">Ideation</h2>
            <p>
            Running from Friday 13th May - Saturday 18 June, teams regulary met on White City Campus 
            and were led through a design process typical of industry. Not only working on conceptual designs, 
            the opportunity to develop pratical workshop skills arose having access the ​facilities at the White City 
            Advanced Hackspace, including 3D Printers, Laser Cutting and traditional manufacturing techniques. 
            This allowed for a range of rapid protoypes and advancement of alternative sculptures shapes to be practically validated.
            </p>
          </div>
        {/if}

        {#if node === 'delivery'}
          <div transition:fade class="absolute top-0 flex flex-col space-y-5">
            <h2 class="text-lg">Delivery</h2>
            <p>
            The final task of the challenge required groups to present their concept to competitors and a 
            panel of judge who assesed the winners, including award winning artists, designers, academics, 
            and commentators. A £1000 offer in prize money donated by the Imperial President’s Community 
            Fund to support the construction of the sculpture. 

            </p>
          </div>
        {/if}
      </div>
    </div>

    <div class="flex w-full h-full justify-center items-center">
      <div
        class="flex w-full h-full justify-center items-center pt-20 "
      >
        <div class="relative top-0 md:h-[250px] md:w-[750px] w-[365px] h-[350px] "> <!-- changing this to absolute changes everything -->
         

          <img src="static/hwdi/nodes3.png" class="md:visible invisible" alt="nodes">
          <img src="static/hwdi/halfnodeL.png" class="visible md:invisible pb-20" alt="nodes">
          <img src="static/hwdi/halfnodeR.png" class="visible md:invisible" alt="nodes">

          <button
            class="group flex items-center justify-center absolute md:left-[3px] left-[80px] md:top-[4px] top-[34px] w-[61px] h-[60px] rounded-full bg-black hover:bg-transparent text-black hover:text-white transition-colors"
            on:click={() => (node = 'brief')}
          >
            <div
              class="group-hover:text-white absolute text-transparent translate-y-20  transition-all select-none pointer-events-none"
            >
              <h1 class="text-xl xl:text-3xl">Brief</h1>
            </div>
            <Icon src={Plus} width="24" />
          </button>
          <button
            class="group flex items-center justify-center absolute md:left-[231px] md:top-[4px] left-[302px] top-[34px] w-[61px] h-[60px] rounded-full bg-black hover:bg-transparent text-black hover:text-white transition-colors"
            on:click={() => (node = 'discover')}
          >
            <div
              class="group-hover:text-white absolute text-transparent translate-y-20  transition-all select-none pointer-events-none"
            >
              <h1 class="text-xl xl:text-3xl">Discover</h1>
            </div>
            <Icon src={Plus} width="24" />
          </button>
          <button
            class="group flex items-center justify-center absolute md:left-[459px] md:top-[4px] left-[222px] top-[170px]  w-[61px] h-[60px] rounded-full bg-black hover:bg-transparent text-black hover:text-white transition-colors"
            on:click={() => (node = 'ideation')}
          >
            <div
              class="group-hover:text-white absolute text-transparent translate-y-20  transition-all select-none pointer-events-none"
            >
              <h1 class="text-xl xl:text-3xl">Ideation</h1>
            </div>
            <Icon src={Plus} width="24" />
          </button>
          <button
            class="group flex items-center justify-center absolute md:left-[687px] md:top-[4px] left-[2px] top-[170px] w-[61px] h-[60px] rounded-full bg-black hover:bg-transparent text-black hover:text-white transition-colors"
            on:click={() => (node = 'delivery')}
          >
            <div
              class="group-hover:text-white absolute text-transparent translate-y-20  transition-all select-none pointer-events-none"
            >
              <h1 class="text-xl xl:text-3xl">Deliver</h1>
            </div>
            <Icon src={Plus} width="24" />
          </button>
        </div>
      </div>
    </div>
</section>

<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 192 404"
  class="absolute inset-0 w-full h-full -z-50"
>
  <defs>
    <clipPath id="wwd-clip">
      <path
        d="M159.12,157.1a33.12,33.12,0,0,1-13.55-2.89A13.53,13.53,0,0,0,130,157.3L63.9,243.52A13.34,13.34,0,0,0,62,259.07a33,33,0,0,1-2.49,36.17,8.46,8.46,0,0,0,.32,10.61l29.4,34.35a8.32,8.32,0,0,0,10.29,1.86,33.18,33.18,0,1,1-11.21,9.77,8.23,8.23,0,0,0-.46-10.16L58.14,307a8.54,8.54,0,0,0-10.34-2,33.09,33.09,0,1,1-.92-59.79A13.39,13.39,0,0,0,62.26,242l66.08-86.19a13.37,13.37,0,0,0,1.89-15.58,33.22,33.22,0,0,1-2.18-27.71,13.14,13.14,0,0,0-4.27-14.86L77.72,61.36A13.42,13.42,0,0,0,62,60.71,33.09,33.09,0,1,1,74.83,44.36a13.48,13.48,0,0,0,4.3,15.22l45.93,36.15a13.47,13.47,0,0,0,15.79.61,33.13,33.13,0,1,1,18.27,60.76Z"
      />
    </clipPath>
  </defs>
</svg>







<!-- <svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 970.93 85.86"
  class="absolute inset-0 w-full h-full -z-50"
>
  <defs>
    <clipPath id="wwd-clip">
      <path
        d="M935.93,0h-16c-.38,.29-.73,.73-1.16,.83-16.24,3.9-26.81,13.88-32.13,29.62-2.53,7.48-7.7,11.27-15.72,11.45-8.32,.19-16.65,.14-24.97,.2h0c-40.33,0-80.66,0-120.98,0h0c-10.97-.06-21.93-.11-32.9-.18-10.02-.06-14.89-3.52-18.25-12.9-2.74-7.64-7.13-14.1-13.42-19.36-6.01-5.03-13.15-7.46-20.44-9.66h-14c-.66,.36-1.33,.72-1.99,1.08-16.16,3.21-26.36,13.18-31.94,28.26-3.25,8.79-8.26,12.52-17.55,12.6-8.16,.07-16.32,.1-24.48,.15-24.33,0-48.67,0-73,0-23,0-45.99,0-68.99-.01h0c-3.66-.05-7.32-.12-10.98-.14-9.77-.04-14.82-3.49-18.06-12.56-4.16-11.66-11.6-20.3-23.03-25.35h0c-2.89-2.4-6.9-2.02-9.96-4.01h-15c-5.9,1.82-11.86,3.49-16.98,7.15,0,0,0,0,0,0-6.79,4.44-12.57,10.14-14.98,17.82-4.05,12.93-12.01,18.86-25.55,17.03-.16-.02-.33,.02-.5,.03h0c-16.01,0-32.01,.01-48.02,.02h0s0,0,0,0c-18.67,.01-37.34,.02-56.01,.03h0s0,0,0,0c-20.66,0-41.32,0-61.97,0h0c-.83-.04-1.66-.12-2.49-.13-13.7-.17-16.14-1.95-21.35-14.77-4.95-12.19-13.51-20.72-26.16-24.9h0s0,0,0,0c-2.32-.77-4.65-1.53-6.97-2.3h-14C18.76,.35,.96,18.55,0,34.94v15.97c1.08,4.42,1.35,8.99,3.82,13.11,7.37,12.31,17.51,20.33,32.17,21.83h14c.66-.36,1.33-.72,1.99-1.08h0c15.36-2.97,25.44-12.27,31.22-26.41,4.52-11.07,7.65-13.4,19.76-13.48,1.33,0,2.66-.09,3.99-.13,20.66,0,41.32,0,61.97,0,18.67,.01,37.34,.02,56.01,.03,16.01,0,32.01,.02,48.02,.02h0c1,.03,2,.09,2.99,.1,15.06,.1,16.11,1.28,22.4,15.24,5.39,11.95,14.24,20.64,27.55,23.82,0,0,0,0,0,0,.93,1.53,3.19,.21,4.05,1.87h16c.62-1,1.72-.8,2.64-1.09,6.05-1.84,11.97-3.93,16.43-8.75,7.36-4.71,10.97-12.07,13.95-19.82,2.97-7.72,7.6-11.15,15.61-11.25,4.46-.06,8.93-.1,13.39-.15h0c23,0,45.99,0,68.99-.01h0s0,0,0,0c24.33,0,48.67,0,73,0h0s0,0,0,0c8.31,.05,16.62,.09,24.94,.14,9.55,.06,13.93,3.19,17.2,11.99,2.76,7.41,6.98,13.77,13.06,19.05,5.82,5.04,12.83,7.3,19.76,9.91h16c.93-1.59,3.16-.42,4.13-1.94h0c14-4.06,23.52-12.96,28.54-26.57,3.39-9.18,7.65-12.36,17.43-12.42,11.31-.07,22.61-.12,33.92-.18,10.79,.05,21.57,.15,32.36,.15,29.54-.02,59.08-.09,88.62-.14h0s0,0,0,0c8.14,.05,16.29,.08,24.43,.17,9.12,.1,13.6,3.37,16.71,11.98,2.76,7.64,7.19,14.09,13.45,19.38,5.71,4.83,12.65,6.94,19.39,9.58h15c17.65-.99,34.69-17.38,36-34.94v-15.97c-1.13-16.6-18.37-33.82-35-34.94ZM56.9,75.5c-.44-.23-.87-.35-1.29-.41,.61-.23,1.2-.49,1.79-.75-.22,.33-.4,.71-.5,1.16Zm3.33-63.04c.14-.03,.28-.05,.43-.09,.07-.16,.11-.31,.16-.47,.02,.13,.05,.26,.06,.4,.02,.22,.09,.41,.14,.61-.26-.16-.52-.3-.78-.45Zm255.84,3.29c0-.21-.01-.43-.06-.66,.06,.05,.1,.11,.16,.16,.19,.01,.37,0,.55,0-.22,.17-.44,.34-.65,.51Zm10.96,60.57c-.09-.33-.24-.59-.41-.82,.62,.21,1.24,.41,1.87,.59-.49,.05-.98,.11-1.46,.23Zm33.26-6.77c-.11,.01-.21,.05-.32,.07,.3-.24,.58-.49,.87-.74,0,.32,.02,.66,.15,1.04,0,.02,0,.03,0,.04-.23-.14-.47-.28-.71-.41Zm238.71-26.73c-.04-7.05,2.23-13.99,6.69-19.9-4.1,5.6-6.56,12.46-6.69,19.9Zm20.12-30.91s.07-.04,.1-.06c1.34-.67,2.94-1.04,3.57-2.6,.03,.03,.05,.06,.08,.09,.71,.38,1.42,.47,2.14,.44-2.05,.53-4.01,1.25-5.9,2.12Zm274.06,32.91c0,2.01,.17,3.99,.48,5.91-.69-2.78-1.04-5.69-.97-8.69,.4-17.39,16.18-35.2,35.4-34.06-19.45,1.03-34.91,17.13-34.91,36.84Z"
      />
    </clipPath>
  </defs>
</svg> -->



<!-- static/projects/sculpture/Sculpture Challenge Draft 03.mov -->

<div class= "flex w-full relative flex-col h-1/4 sm:h-full">
  
  <!-- {#if node === ''}
    <div class = "flex w-full h-full justify-center gap-x-10">
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 absolute top-[10%] order-first z-[3] scale-150"
      style="background: url(/projects/sculpture/sculpture.jpg); background-size: cover;" />
    </div>
  {/if}   -->

  {#if node === 'brief'}
    <div class = "flex w-full h-full justify-center gap-x-10 scale-110">
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 absolute top-[15%] order-first z-[3] imagepre_2"
      style="background: url(/projects/sculpture/brief1.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[2] hover:z-[4] imagepre_1"
      style="background: url(/projects/sculpture/brief2.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[1] hover:z-[4] imagepre_3"
      style="background: url(/projects/sculpture/brief3.jpg); background-size: cover;" />
    </div>
    
  {/if}

  {#if node === 'ideation'}
  <div class = "flex w-full h-full justify-center gap-x-10 scale-110">
    <div
    class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 absolute top-[15%] order-first z-[3] imagepre_2"
    style="background: url(/projects/sculpture/ideation1.jpg); background-size: cover;" />
    <div
    class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[2] hover:z-[4] imagepre_1"
    style="background: url(/projects/sculpture/ideation2.jpg); background-size: cover;" />
    <div
    class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[1] hover:z-[4] imagepre_3"
    style="background: url(/projects/sculpture/ideation3.jpg); background-size: cover;" />
  </div>
  {/if}
  
  {#if node === 'discover'}
    <div class = "flex w-full h-full justify-center gap-x-10 scale-110">
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 absolute top-[15%] order-first z-[3] imagepre_2"
      style="background: url(/projects/sculpture/discover1.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[2] hover:z-[4] imagepre_1"
      style="background: url(/projects/sculpture/discover2.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[1] hover:z-[4] imagepre_3"
      style="background: url(/projects/sculpture/discover3.jpg); background-size: cover;" />
    </div>
  {/if}

  {#if node === 'delivery'}
    <div class = "flex w-full h-full justify-center gap-x-10 scale-110">
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 absolute top-[15%] order-first z-[3] imagepre_2"
      style="background: url(/projects/sculpture/delivery1.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[2] hover:z-[4] imagepre_1"
      style="background: url(/projects/sculpture/delivery2.jpg); background-size: cover;" />
      <div
      class="rounded-full w-40 md:w-60 xl:w-80 h-40 md:h-60 xl:h-80 relative absolute z-[1] hover:z-[4] imagepre_3"
      style="background: url(/projects/sculpture/delivery3.jpg); background-size: cover;" />
    </div>
  {/if}

</div>

<!-- TRIAL OF OUR IMPACT -->



<div class="relative flex w-screen flex-col items-center min-h-screen">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="absolute inset-0 -z-50 w-screen h-screen"
  >
    <defs>
      <clipPath id="manifesto_clip">
        <circle cx="50%" cy="75%" r={$manifesto + 5 + "%"} />
      </clipPath>
    </defs>
  </svg>

  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="absolute inset-0 -z-50 w-screen h-screen"
  >
    <defs>
      <clipPath id="manifesto_button_clip">
        <circle cx="50%" cy="75%" r={(100 - $manifesto) / 21 + "%"} />
      </clipPath>
    </defs>
  </svg>

  <OnMount>
    <div class="sticky top-0 left-0 w-full h-screen z-40">
      <div
        class="gradient absolute top-0 left-0 w-full h-3/4 flex items-center justify-center z-40"
        style="clip-path: url(#manifesto_clip)"
        in:fly={{ y: 150, duration: 1500, delay: 3000 }}
      />

      <div
        class="absolute top-0 left-0 w-full h-full flex items-center justify-center z-40 cursor-pointer"
        on:click={() => (manifesto_open = !manifesto_open)}
        style="background: black; clip-path: url(#manifesto_button_clip)"
        in:fly={{ y: 150, duration: 1500, delay: 3000, opacity: 1 }}
      />

      <div
        id="expand_text"
        class="absolute left-1/2 xl:top-1/2 top-2/3 -translate-x-1/2"
        in:fly={{ y: 250, duration: 1500, delay: 2000 }}
      >
        <p class=" xl:pt-9">Click circle to expand</p>
      </div>
    </div>
  </OnMount>

  <div
    class="{manifesto_open &&
      'text-black'} absolute top-0 flex flex-col w-full h-screen items-center justify-center space-y-1 px-4 xl:px-32"
  >
    <OnMount>
      <h1 class="z-40" in:fade={{ duration: 800, delay: 0 }}>
        DreamTeam Impact
      </h1>
    </OnMount>
  </div>

  {#if manifesto_open}

    <div
      class="text-black text-center absolute align-top top-1/4 max-w-[800px] h-20% items-center justify-center px-4 xl:px-32 z-40"
    >
      <h2>With the success of the challenge and enjoyment of those involved, it has promoted future events at Imperial aimed at communicating Imperial’s brand through artwork and technology. </h2>
      <h2>Being designed by students for everyone who visits the campus, the future sculpture would see its legacy in all manner of social benefits from wayfinding to a sense of place and belonging, to simply be an inspiring landmark of Imperial.</h2>
    </div>

  {/if}
</div>




