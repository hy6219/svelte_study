<script>
	let firstname = "jisoo";//이름
	let lastname = "jeong";//성

	$: fullname = `${firstname} ${lastname}`;

	let beltColour = "black";
	let btnClickCnt = 0;
	$: console.log(beltColour);

	const handleClick = ()=>{
		++btnClickCnt;
		beltColour = btnClickCnt%2==1?"black":"blue";
	};

	const handleInput = (e)=>{
		beltColour = e.target.value;
	};
</script>

<main>
	<h1>{fullname}</h1>
	<p style="color:{beltColour}">{beltColour} belt</p>
	<!--사용자 입력받기-->
	<!--value,bind:value : 양방향 바인딩-->
	<input type="text" bind:value="{firstname}">
	<input type="text" bind:value = "{lastname}">
	<input type="text" bind:value="{beltColour}">
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