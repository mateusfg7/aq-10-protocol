<script lang="ts">
	import ChoiceSelector from '$lib/components/choice-selector.svelte';

	let questions = [
		{
			question: 'Costumo notar pequenos sons quando outros não percebem',
			reverseWeight: false,
			points: 0
		},
		{
			question:
				'Eu geralmente me concentro mais no todo de uma imagem, ao invés de pequenos detalhes',
			reverseWeight: true,
			points: 0
		},
		{
			question: 'Acho fácil fazer mais de uma coisa de uma só vez',
			reverseWeight: true,
			points: 0
		},
		{
			question: 'Se houver uma interrupção, posso voltar para o que eu estava fazendo muito rápido',
			reverseWeight: true,
			points: 0
		},
		{
			question: 'Acho fácil “ler nas entrelinhas” quando alguém esta falando comigo',
			reverseWeight: true,
			points: 0
		},
		{
			question: 'Eu sei dizer se alguém que está me ouvindo está ficando entediado',
			reverseWeight: true,
			points: 0
		},
		{
			question:
				'Quando estou lendo uma história, acho difícil descobrir as intenções dos personagens',
			reverseWeight: false,
			points: 0
		},
		{
			question:
				'Gosto de coletar informações sobre categorias de coisas (por exemplo, tipos de carro, tipos de pássaros, tipos de trem, tipos de planta, etc.)',
			reverseWeight: false,
			points: 0
		},
		{
			question:
				'Acho que é fácil descobrir o que alguém está pensando ou sentindo apenas olhando para o rosto da pessoa',
			reverseWeight: true,
			points: 0
		},
		{ question: 'Acho difícil entender as intenções das pessoas', reverseWeight: false, points: 0 }
	];
</script>

<div class="flex flex-col max-w-[40rem] gap-16 pb-52">
	{#each questions as { points, question, reverseWeight }, index (question)}
		<ChoiceSelector index={index + 1} {reverseWeight} title={question} bind:points />
	{/each}
</div>
