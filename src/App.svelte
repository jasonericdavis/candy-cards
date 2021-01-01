<script>
	import ColorCard from './ColorCard.svelte'
	import deck from './deck'
	import { slide } from 'svelte/transition';

	let cardIndex = 0
	let card = deck[cardIndex]

	const getNextCard = () => {
		console.log(`I am the click handler`)
		cardIndex = (cardIndex >= deck.length - 1)? 0 : cardIndex + 1
		card = deck[cardIndex]
	}
	export let name;
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
</style>

<main>
	<h1>{name}!</h1>
	<div on:click={getNextCard}  transition:slide="{{delay: 250, duration: 1000}}">
		{#if card.type === 'color'}
			<ColorCard {card} />
		{:else}
			<div>TODO: create the other types of blocks</div>
		{/if}
	</div>
</main>