<script>
	import ColorCard from './ColorCard.svelte';
	import CandyCard from './CandyCard.svelte';
	import cards from './deck';
	import { fade } from 'svelte/transition';

	let cardIndex
	let card
	let deck = [...cards]
	let unique = {} // unique is used to recreate the card component 
	export let name;
	
	const getNextCard = () => {
		/* 
			if the deck still has cards 
			select a random card from the deck. If not then "shuffle"
			by re-adding the cards
		*/
		if(deck.length < 1 ) deck = [...cards]
		cardIndex = Math.floor(Math.random() * deck.length)
		card = {...deck[cardIndex]}
		deck = deck.filter((card, index) => index != cardIndex)
		console.table(deck)
		unique = {} 
	}
</script>

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
		font-size: 1.5em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.card {
		box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
		margin-left: auto;
		margin-right: auto;
		padding-top: 15px;
		padding-bottom: 10px;
		background-color: #F8F8F8;
		max-width: 500px;
	}

	:global(:root) {
		--block-color-purple: #AB47BC;
		--block-color-red: #F44336;
		--block-color-yellow: #FFF176;
		--block-color-green: #81C784;
		--block-color-blue: #5DADE2;
		--block-color-orange: #FFA726;
	}
</style>

<main>
	<h1>{name}!</h1>	
	{#if !card}
		<div>Welcome to Candy Cards. Click to start</div>
		<button on:click={getNextCard}>Start</button>
	{:else}
		{#key unique}
		<div class="card" >
			<div on:click={getNextCard} in:fade="{{delay: 500, duration: 500}}" out:fade="{{delay: 50, duration: 500}}">
				{#if card.type === 'color'}
					<ColorCard {card} />
				{/if}
				{#if card.type === 'candy'}
					<CandyCard {card} />
				{/if}
			</div>
		</div>
		{/key}
	{/if}
</main>