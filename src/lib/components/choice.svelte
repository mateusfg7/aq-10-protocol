<script lang="ts">
	export let selected: string;
	export let option: Option;

	const optionTitles: { [key in Option]: String } = {
		bad_1: 'Discordo plenamente',
		bad_0: 'Discordo parcialmente',
		good_0: 'Concordo parcialmente',
		good_1: 'Concordo plenamente'
	};
</script>

<button
	on:click={() => (selected = option)}
	data-selected={selected === option}
	class:bad_1={option === 'bad_1'}
	class:bad_0={option === 'bad_0'}
	class:good_0={option === 'good_0'}
	class:good_1={option === 'good_1'}
	class="flex items-center justify-center flex-1 p-2 text-center transition-colors border-r cursor-pointer select-none border-neutral-200 data-[selected='true']:font-bold"
>
	{optionTitles[option]}
</button>

<style lang="postcss">
	.bad_1 {
		@apply hover:bg-red-200 hover:text-red-950 data-[selected='true']:text-white data-[selected='true']:bg-red-700;
	}
	.bad_0 {
		@apply hover:bg-red-50 hover:text-red-950 data-[selected='true']:text-white data-[selected='true']:bg-red-500;
	}
	.good_0 {
		@apply hover:bg-green-50 hover:text-green-950 data-[selected='true']:text-white data-[selected='true']:bg-green-500;
	}
	.good_1 {
		@apply hover:bg-green-200 hover:text-green-950 data-[selected='true']:text-white data-[selected='true']:bg-green-700;
	}
</style>
