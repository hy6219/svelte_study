<script>
	let name = "jisoo";
	let beltColour = "black";
	let btnClickCnt = 0;

	const handleClick = ()=>{
		++btnClickCnt;
		beltColour = btnClickCnt%2==1?"black":"blue";
	};

	const handleInput = (e)=>{
		beltColour = e.target.value;
	};
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>{beltColour} belt</p>
	<button on:click="{handleClick}">update belt colour</button>
	<!--사용자 입력받기-->
	<input type="text" on:input="{handleInput}">
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