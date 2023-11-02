<script lang="ts">
	import Choice from './choice.svelte';

	export let reverseWeight: boolean;
	export let title: string;
	export let points: number;
	export let index: number;

	let choice: string;

	const values: { option: Option; weight: number }[] = [
		{ option: 'bad_1', weight: reverseWeight ? 1 : 0 },
		{ option: 'bad_0', weight: reverseWeight ? 1 : 0 },
		{ option: 'good_0', weight: reverseWeight ? 0 : 1 },
		{ option: 'good_1', weight: reverseWeight ? 0 : 1 }
	];

	$: points = values.filter((value) => value.option === choice)[0]?.weight;
</script>

<div class="flex flex-col gap-8">
	<span class="text-2xl">
		<span class="font-bold">{index}.</span>
		<span>{title}</span>
	</span>
	<div class="flex overflow-hidden border rounded-lg border-neutral-400">
		{#each values as value}
			<Choice bind:selected={choice} option={value.option} />
		{/each}
	</div>
</div>
