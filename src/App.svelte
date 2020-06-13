<script>
	import Modal from './Modal.svelte';

	let people  = [
		{ name: 'Yoshi', beltColor: 'black', age: 25, id: 1},
		{ name: 'Mario', beltColor: 'yello', age: 31, id: 2},
		{ name: 'Zelda', beltColor: 'green', age: 28, id: 3}
	]

	const handleClick = (id) => {
		people = people.filter(person => person.id !== id);
	}

	let showModal = false;
	
	const toggleModal = () => { showModal = !showModal;}

</script>


<Modal {showModal} on:click={toggleModal}>
	<h3>Add a New Person</h3>
	<form>
		<input type="text" placeholder="name">
		<input type="text" placeholder="belt color">
		<button>Add Person</button>
	</form>

</Modal>
<main>

	<button on:click={toggleModal}>Toggle modal</button>

	<div>
		{#each people as person (person.id)}
			<div>
				<h4>{person.name}</h4>
				<p>{person.age} years old, {person.beltColor} belt</p>
				{#if person.beltColor === 'black'}
					<p><strong>Master!</strong></p>
				{/if}
				<button on:click={()=>handleClick(person.id)}>
					Delete
				</button>
			</div>
		{:else}
			<p>Ther are no people to show</p>
		{/each}
		
	</div>
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