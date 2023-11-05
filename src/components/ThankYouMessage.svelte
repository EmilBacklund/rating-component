<script lang="ts">
	import illustration from '$lib/images/illustration-thank-you.svg';
	export let isValid: boolean;
	export let selectedRating: number | undefined;

	function getMessageByRating(rating: number | undefined): string {
		switch (rating) {
			case 1:
				return `A ${rating}-star day, huh? Seems like we've got some serious leveling up to do! Drop us a line and help us quest for that epic 5-star rating.`;
			case 2:
				return `A ${rating}-star moment? We're scratching our heads wondering where we slipped up. Help us crack the code to a 5-star experience, and we promise to hustle harder than a squirrel before winter! 🌰💪`;
			case 3:
				return `A middle-of-the-road ${rating}! Not too shabby, but we're craving those extra stars like cookies. Got tips? We're all ears! 🍪`;
			case 4:
				return `Yay! A ${rating} is pretty darn good, but why stop there? We're on the edge of our seats for that 5-star performance! 🚀`;
			case 5:
				return `A perfect ${rating}! 🎉 We're throwing confetti and popping the non-alcoholic champagne as we speak! You're officially our favorite person today.`;
			default:
				return 'Select a rating to see some magic happen!';
		}
	}

	$: messageToDisplay = getMessageByRating(selectedRating);
</script>

<section
	class="flex flex-col items-center justify-center text-center absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-full px-6 transition-opacity duration-1000 {!isValid
		? 'opacity-0 pointer-events-none -z-10'
		: 'opacity-100 pointer-events-auto z-10'}"
>
	<img class="pb-6 sm:pb-8" src={illustration} alt="illustration" />
	<p
		class="text-sm sm:text-[15px] sm:leading-[24px] leading-[22px] text-[#FC7614] bg-[#262E38] rounded-[22.5px] px-5 py-1"
	>
		You selected {selectedRating} out of 5
	</p>
	<h2
		class="font-bold text-2xl sm:text-[28px] sm:leading-[35px] pt-6 sm:pt-8 pb-[17px] sm:pb-[15px]"
	>
		{#if selectedRating <= 2}
			We're Listening!
		{:else}
			Thank you!
		{/if}
	</h2>
	<p class="text-sm sm:text-[15px] sm:leading-[24px] leading-[22px] text-[#969FAD]">
		{messageToDisplay}
	</p>
</section>
