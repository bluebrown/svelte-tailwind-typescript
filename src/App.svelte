<script lang="ts">
  import './assets/Tailwindcss.svelte';
  import Excel2MD from './components/Excel2MD.svelte';
  import Navbar from './components/Navbar.svelte';
  import Sidebar from './components/Sidebar.svelte';
  let sidebarHidden = true;
</script>

<style>

</style>

<main class="flex w-full h-full min-w-0 min-h-0">
  <div class="flex flex-col flex-1 min-h-0 min-w-0">
    <header class="w-full min-w-0 border-b p-3 pb-5 overflow-auto bg-gray-100 flex flex-col">
      <Navbar end={[{ label: 'Sidebar', onclick: () => (sidebarHidden = !sidebarHidden) }]} />
      <div class="flex flex-wrap min-h-0 min-w-0" />
    </header>
    <main class="min-h-0 min-w-0 w-full flex-1 flex overflow-auto relative">
        <Excel2MD />
    </main>
  </div>
  <Sidebar hidden={sidebarHidden} />
</main>
