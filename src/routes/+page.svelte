<script lang="ts">
	import ChoiceSelector from '$lib/components/choice-selector.svelte';

	let total: number | undefined;

	let questions: { question: string; reverseWeight: boolean; points: number | undefined }[] = [
		{
			question: 'Costumo notar pequenos sons quando outros não percebem',
			reverseWeight: false,
			points: undefined
		},
		{
			question:
				'Eu geralmente me concentro mais no todo de uma imagem, ao invés de pequenos detalhes',
			reverseWeight: true,
			points: undefined
		},
		{
			question: 'Acho fácil fazer mais de uma coisa de uma só vez',
			reverseWeight: true,
			points: undefined
		},
		{
			question: 'Se houver uma interrupção, posso voltar para o que eu estava fazendo muito rápido',
			reverseWeight: true,
			points: undefined
		},
		{
			question: 'Acho fácil “ler nas entrelinhas” quando alguém esta falando comigo',
			reverseWeight: true,
			points: undefined
		},
		{
			question: 'Eu sei dizer se alguém que está me ouvindo está ficando entediado',
			reverseWeight: true,
			points: undefined
		},
		{
			question:
				'Quando estou lendo uma história, acho difícil descobrir as intenções dos personagens',
			reverseWeight: false,
			points: undefined
		},
		{
			question:
				'Gosto de coletar informações sobre categorias de coisas (por exemplo, tipos de carro, tipos de pássaros, tipos de trem, tipos de planta, etc.)',
			reverseWeight: false,
			points: undefined
		},
		{
			question:
				'Acho que é fácil descobrir o que alguém está pensando ou sentindo apenas olhando para o rosto da pessoa',
			reverseWeight: true,
			points: undefined
		},
		{
			question: 'Acho difícil entender as intenções das pessoas',
			reverseWeight: false,
			points: undefined
		}
	];

	function getTotal() {
		const undefinedQuestions = questions.filter((question) => question.points === undefined);

		if (undefinedQuestions.length > 0) return;

		total = questions
			.map((question) => question.points)
			.reduce((accumulator, currentValue) => (accumulator as number) + (currentValue as number));
	}
</script>

<div class="flex flex-col max-w-[40rem] gap-32 pb-52">
	<div class="flex flex-col gap-16">
		{#each questions as { points, question, reverseWeight }, index (question)}
			<ChoiceSelector index={index + 1} {reverseWeight} title={question} bind:points />
		{/each}
	</div>
	<div class="space-y-10">
		<div class="flex justify-between text-2xl md:text-4xl">
			<span>Pontos</span>
			<span
				data-use-gradient={total && total > 5}
				class="text-4xl md:text-6xl font-bold gradient bg-clip-text data-[use-gradient='true']:text-transparent"
			>
				{#if total}
					{total}
				{:else}
					?
				{/if}
			</span>
		</div>
		<button
			on:click={getTotal}
			class="w-full p-4 text-xl font-bold text-white transition-colors bg-blue-500 rounded-lg md:text-3xl hover:bg-blue-600 active:bg-blue-800"
			>Calcular</button
		>
	</div>
</div>

<style>
	.gradient {
		background-image: linear-gradient(
			to right,
			#ff1c18,
			#ff6e04,
			#ffde0e,
			#1ae489,
			#08cef7,
			#4953fe,
			#9633e1,
			#ea1b5f
		);
	}
</style>
