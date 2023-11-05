<script lang="ts">
	import iconStar from '$lib/images/icon-star.svg';
	import Rating from './Rating.svelte';
	import ThankYouMessage from './ThankYouMessage.svelte';

	let selectedRating: number | undefined;
	let isValid = false;

	function handleRatingSelect(event: CustomEvent<number>) {
		selectedRating = event.detail;
	}

	function handleSubmit() {
		if (selectedRating) {
			isValid = true;
		}
	}
</script>

<section
	class="max-w-[327px] sm:max-w-[412px] relative from-[#232A34] to-[#181E27] bg-gradient-to-b pb-8 pt-6 px-6 sm:p-8 rounded-[30px]"
>
	<div
		class="transition-opacity duration-150 {!isValid
			? 'opacity-100 pointer-events-auto z-10'
			: 'opacity-0 pointer-events-none -z-10'}"
	>
		<div
			class="rounded-full mb-4 sm:mb-[30px] h-10 w-10 sm:w-12 sm:h-12 bg-[#262E38] flex items-center justify-center"
		>
			<img src={iconStar} alt="star icon" class="w-[13.96px] h-[13.33px] sm:w-[16.75px] sm:h-4" />
		</div>
		<h1 class="text-2xl sm:text-[28px] sm:leading-[35px] font-bold pb-[17px] sm:pb-[15px]">
			How did we do?
		</h1>
		<p class="leading-[22px] text-sm sm:text-[15px] sm:leading-6 pb-6 text-[#969FAD]">
			Please let us know how we did with your support request. All feedback is appreciated to help
			us improve our offering!
		</p>
		<Rating on:selectedRating={handleRatingSelect} />
		<button
			on:click={() => {
				handleSubmit();
			}}
			class="h-[45px] w-full bg-[#FC7614] rounded-[22.5px] font-bold text-sm sm:text-[15px] tracking-[1.87px] sm:tracking-[2px] transition-colors duration-500 hover:bg-white hover:text-[#FC7614]"
			>SUBMIT</button
		>
	</div>
	<ThankYouMessage {isValid} {selectedRating} />
</section>
