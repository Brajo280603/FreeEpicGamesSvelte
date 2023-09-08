<script>
  import { onDestroy, onMount } from "svelte";
  import GameCards from "../lib/game-cards.svelte";

	async function apicall(){
		let res = await fetch("/api")


		return await res.json()
	}
	

	let games = { 
		currents:[],
		nexts:[]
	};
	onMount(()=>{
	 games = apicall();
	})
	onDestroy(()=>{
		games = { 
		currents:[],
		nexts:[]
	};
	})
</script>
<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->

<div class="container h-full mx-auto flex justify-center items-center mt-5">
	
		
	{#await games}
		<h1 class="text-5xl font-bold text-center">Loading...</h1>
	{:then games} 
		<div class="h-full  grid lg:grid-cols-3 gap-5 sm:grid-cols-2 grid-cols-1">
			{#each games.currents as game }
				<GameCards gameName={game.name} gameDesc={game.desc} gameIcon={game.img} gameLink={game.link}></GameCards>
			{/each}
			{#each games.nexts as game }
				<GameCards gameName={game.name} gameDesc={game.desc} gameIcon={game.img} gameLink={game.link}></GameCards>
			{/each}
		</div>
	{:catch error}
		<h1 class="text-5xl font-bold text-center">Sorry! Server Error, Please Retry...</h1>
	{/await}
	
</div>
