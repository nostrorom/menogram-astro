<script lang="ts">
	import { slide } from 'svelte/transition';
	import type { Content } from '../../types/content';

	export let open: boolean;

	export let content: Content;
</script>

{#if content.title}
	<div class="text-fuchsia-500 font-extrabold text-lg font-title tracking-widest uppercase pt-12">
		{content.title}
	</div>
{/if}

{#if content.subtitle}
	<div class="text-orange-500 font-extrabold font-title tracking-widest uppercase pt-4">
		{content.subtitle}
	</div>
{/if}

{#if content.q}
	<div
		on:click={() => {
			open = !open;
		}}
		class="flex italic rounded-md opacity-75 my-4 leading-relaxed cursor-pointer hover:text-white"
	>
		<div class="w-11/12">
			{content.q}
		</div>
		<div class="w-1/12 flex items-center justify-end">
			{#if !open}
				<div class="bg-teal-600 h-2 w-2 rounded-full" />
			{/if}
		</div>
	</div>
	{#if content.a && open}
		<div
			transition:slide={{ duration: 300 }}
			class="px-3 mb-2 border-l-2 border-teal-600 text-indigo-300 leading-relaxed"
		>
			{content.a}
		</div>
	{/if}
{/if}
