<script>
	let name = "world!";
	let beltColour = "black";
	let btnClickCnt = 0;

	const handleClick = ()=>{
		++btnClickCnt;
		beltColour = btnClickCnt%2==1?"orange":"black";
	};
</script>

<main>
	<h1>Hello {name} svelte!</h1>
	<p>{beltColour} belt</p>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click="{handleClick}">update belt colour</button>
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