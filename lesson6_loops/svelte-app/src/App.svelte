<script>
	let people = [
		{name : 'yoshi',belt_colour:'black',age:25,id:1},
		{name : 'mario',belt_colour:'blue',age:45,id:2},
		{name : 'luigi',belt_colour:'orange',age:35,id:3}
	];
</script>

<main>
	<!-- <div>
		<h4>{people[0].name}</h4>
		<p>{people[0].belt_colour}</p>
	</div>
	<div>
		<h4>{people[1].name}</h4>
		<p>{people[1].belt_colour}</p>
	</div>
	<div>
		<h4>{people[2].name}</h4>
		<p>{people[2].belt_colour}</p>
	</div> -->
	<!-- {#each  people as person}
		<h4>{person.name}</h4>
		<p>{person.age}</p>
		<p>{person.belt_colour}</p>
	{/each} -->
	<!--unique key인 id로 접근-->
	{#each  people as person(person.id)}
		<h4>{person.name}</h4>
		<p>{person.age}</p>
		<p>{person.belt_colour}</p>
		{:else}
			<p>There are no people to show...</p>
	{/each}
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