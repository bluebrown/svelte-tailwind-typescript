<script lang="ts">
  import CSVExport from '../components/CSVExport.svelte';
  import marked from 'marked';
  let value = '';
  let showHtml = false;
  let data = [];
  const pasted = (e) => {
    let pasted = e.clipboardData.getData('text');
    let [h, ...b] = pasted.split('\n');
    h = h.split('\t');
    b = b.map((l) => l.split('\t'));
    data = [h, ...b];
    let d = h.map(() => ':-:');
    value = [h, d, ...b].map((cell) => cell.join(' | ')).join('\n');
  };
</script>

<style>

</style>

<article class="flex flex-col w-full h-full min-w-0 min-h-0">
  <section class="p-3">
    <h1 class="font-semibold text-3xl">Excel to Markdown</h1>
    <p class="mb-3 text-gray-700">Paste tab divided text here to generate a markdown table</p>
    <textarea rows="10" bind:value class="w-full rounded-md border" on:paste|preventDefault={pasted} />
  </section>
  <hr />
  <section class="flex-1 min-w-0 min-h-0 overflow-auto">
    <header class="p-3 pb-2">
      <button
        on:click={() => (showHtml = !showHtml)}
        class="minor-button">
        Toggle View
      </button>

      <CSVExport {data} />

    </header>
    <div class="p-3 pt-0">
      {#if !showHtml}
        {@html marked(value)}
      {:else}{marked(value)}{/if}
    </div>
  </section>
</article>
