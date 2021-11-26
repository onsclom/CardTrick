<script>
	import CardSelect from './CardSelect.svelte';
	import Card from './Card.svelte';

	let card1="1"
	let suit1="1"
	let card2="2"
	let suit2="1"
	let card3="3"
	let suit3="1"
	let card4="4"
	let suit4="1"
	
	let suits="♣♥♠♦"
	let orderNum=0
	
	let showCard = false
	let showWorks = false
	//1-13 represents A-K cards
	//add first card's value to order num of last 3 cards
	//wrap around value with modulus if needed
	$: calcNum = () => {
		let card1Data = [parseInt(card2), parseInt(suit2), 1]
		let card2Data = [parseInt(card3), parseInt(suit3), 2]
		let card3Data = [parseInt(card4), parseInt(suit4), 3]
		let cards = [card1Data, card2Data, card3Data]
		cards.sort((c1, c2) => {
			if (c1[0]==c2[0])
				return c1[1]-c2[1]
			return c1[0]-c2[0]
		})
		let orderString = `${cards[0][2]}${cards[1][2]}${cards[2][2]}`
		let orderToNum = {
			"123": 1,
			"132": 2,
			"213": 3,
			"231": 4,
			"312": 5,
			"321": 6
		}
		orderNum = orderToNum[orderString]
		return (orderToNum[orderString]-1+parseInt(card1))%13+1
	}
</script>

<main>
	<h1>card trick wow</h1>
	<div class="cardContainer">
		<CardSelect bind:num={card1} bind:suit={suit1}></CardSelect>
		<CardSelect bind:num={card2} bind:suit={suit2}></CardSelect>
		<CardSelect bind:num={card3} bind:suit={suit3}></CardSelect>
		<CardSelect bind:num={card4} bind:suit={suit4}></CardSelect>
	</div>
	
	
	{#if showCard}
		<Card num={calcNum()} bind:suit={suit1}>
		</Card>
<!-- 		{#if showWorks}
			<p>suit = suit of 1st card = {suits[suit1-1]}</p>
			<p>value = value of 1st card + ordering of next 3 cards = {card1} + {orderNum}</p>
		{:else}
			<button on:click={()=>{showWorks=true}}>
				show how it works	
			</button>
		{/if} -->
	{:else}
		<button on:click={()=>{showCard=true}}>
			show face down card	
		</button>
	{/if}
</main>

<style>
	.cardContainer {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}
	main {
		text-align: center;
	}
</style>
