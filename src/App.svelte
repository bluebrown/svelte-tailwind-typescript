<script lang="ts">
	import "./Tailwindcss.svelte";
	import marked from "marked";
	let value = "";
	let showHtml = false;
	const pasted = (e) => {
			let pasted = e.clipboardData.getData('text')
			let [h, ...b] = pasted.split('\n')
			h = h.split('\t')
			let d = h.map(() => '-')
			value = [h, d, ...b.map((l) => l.split('\t'))]
				.map((line) =>  line.join(' | '))
				.join('\n')
		}
</script>

<main class="flex flex-col w-full h-full min-w-0 min-h-0">
	<section class="p-3">
	<h1 class="font-semibold text-3xl">Excel to Markdown</h1>
	<p class="mb-3 text-gray-700"
	>Paste tab divided text here to generate a markdown table</p>
	<textarea 
		rows="10"
		bind:value={value}
		class="w-full rounded-md border"
		on:paste|preventDefault={pasted}
	></textarea>
	</section>
	<hr>
	<section class="flex-1 min-w-0 min-h-0 overflow-auto">
	<header class="p-3 pb-2">
			<button 
				on:click={() => showHtml = !showHtml}
				class="text-xs bg-gray-300 hover:bg-gray-200 px-2 py-1 rounded-sm shadow-sm"
		>Toggle View</button>
	</header>
	<div class="p-3 pt-0">
	{#if !showHtml} 
		{@html marked(value)}
	{:else}
		{marked(value)}
	{/if}
	</div>
</section>
</main>

<style>
</style>