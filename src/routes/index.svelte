<script lang="ts">
  import Menu from "$lib/menu/Menu.svelte";
  import MenuIcon from "$lib/menu/MenuIcon.svelte";
  import Manifesto from "$lib/sections/manifesto.svelte";

  let panelOpen = false;
  let panelContent = "menu";

  let closeMenu = () => (panelOpen = false);
</script>


<div class="w-full h-0 fixed inset-0 flex flex-col justify-between z-50">
  <div class="flex items-center justify-between p-2.5 md:p-5">
    <img src="/dreamteam.svg" alt="dreamteam" width="200" />

    <button
      on:click={() => {
        panelOpen = !panelOpen;
        panelContent = "menu";
      }}
      class="p-2"
    >
      <MenuIcon
        bind:open={panelOpen}
        class="w-6 xl:w-8 {panelOpen &&
          '-rotate-90'} transition-transform duration-300"
      />
    </button>
  </div>
</div>

<main class="space-y-48 xl:space-y-96">
  
  <Manifesto />

</main>

<Menu open={panelOpen && panelContent === "menu"} {closeMenu} />
