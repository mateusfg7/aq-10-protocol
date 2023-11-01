<script lang="ts">
	let choice: string;
</script>

<div class="border border-red-600">
	<div>C acha q é doido?</div>
	<div>
		<div>
			<label for="q1">Absolutamente não</label>
			<input type="radio" name="q1" id="q1" value="q1" bind:group={choice} />
		</div>
		<div>
			<label for="q1">Acho q não</label>
			<input type="radio" name="q2" id="q2" value="q2" bind:group={choice} />
		</div>
		<div>
			<label for="q1">Sei la</label>
			<input type="radio" name="q3" id="q3" value="q3" bind:group={choice} />
		</div>
		<div>
			<label for="q1">Acho q sim</label>
			<input type="radio" name="q4" id="q4" value="q4" bind:group={choice} />
		</div>
		<div>
			<label for="q1">Com certesa</label>
			<input type="radio" name="q5" id="q5" value="q5" bind:group={choice} />
		</div>
	</div>
</div>
