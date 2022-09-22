<script>
	import Modal from './Modal.svelte';

	let showModal = false;

	let people = [
		{ name: 'ms sheila', subtitle: 'code composer', age:44, id: 1 },
		{ name: 'holly', subtitle: 'teen trouble', age:14, id: 2 },
		{ name: 'ben', subtitle: 'little leprechaun', age:8, id: 3 }

	]

	const deletePerson = (id) => {
		people = people.filter((person) => person.id != id)
	}

	let signedIn = 'Who are you?';

	const toggleModal = () => {
		showModal = !showModal;
	}

</script>

<Modal message="You did it!" isCongrats={true} {showModal} on:click={toggleModal}/>
<main>
	<button on:click|once={toggleModal}>Positive message</button>
	<input type="text" bind:value={signedIn}>

	{#if signedIn=='Sheila'}
		{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.subtitle}, {person.age} years old</p>
			<button on:click={() => deletePerson(person.id)}>delete</button>
		</div>
		{:else}
		<p>There are no people to show . . .</p>

		{/each}
	{:else if signedIn=='student'}
		{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.subtitle}, {person.age} years old</p>
		</div>

		{:else}
		<p>There are no people to show . . .</p>
		{/each}

	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>