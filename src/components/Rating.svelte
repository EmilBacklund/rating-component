<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	let selectedRating: number | undefined;
	const rating = [1, 2, 3, 4, 5];
	const dispatch = createEventDispatcher();

	function selectRating(item: number) {
		selectedRating = item;
		dispatch('selectedRating', item);
	}
</script>

<section class="flex justify-between pb-6 sm:pb-8">
	{#each rating as item}
		<button
			class="rounded-full w-[42px] h-[42px] sm:w-[51px] sm:h-[51px] group outline-none bg-[#262E38] text-center text-sm sm:text-base leading-[45px] sm:leading-[55px] font-bold transition-colors duration-500 {selectedRating ===
			item
				? 'bg-[#FC7614] text-white'
				: 'focus:bg-[#7C8798] focus:ring-[#FC7614] focus:ring-2 hover:bg-[#7C8798] text-[#969FAD]'}"
			on:click={() => selectRating(item)}
		>
			<p class="group-hover:text-white group-focus:text-white">{item}</p>
		</button>
	{/each}
</section>
