<script>
	export let website;
	export let layer;
	import noise from '$lib/assets/noise.png';
	import { onMount } from 'svelte';

	function getRandomColor() {
		const letters = '0123456789ABCDEF';
		let color = '#';
		for (let i = 0; i < 6; i++) {
			color += letters[Math.floor(Math.random() * 16)];
		}
		return color;
	}

	function setRandomColor() {
		const spans = document.querySelectorAll('a.' + layer + ' span');
		spans.forEach((span) => {
			span.style.backgroundColor = getRandomColor();
		});
	}

	onMount(setRandomColor);
</script>

<a class={layer} href={website.slug}>
	<div style="background-image: url({noise});">
		<span />
	</div>

	<h3>
		{website.titel}
	</h3>
</a>

<style>
	a.voor,
	a {
		position: relative;
		width: 80%;
		aspect-ratio: 2/1.2;
		text-decoration: none;
		color: black;
	}

	span {
		aspect-ratio: 2/1;
		display: block;
		height: auto;
		mix-blend-mode: color-burn;
		z-index: 10;
		/* filter: blur(3px); */
		width: 100%;
		height: 100%;
	}

	div {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100%;
	}

	a:nth-child(1n) {
		margin-top: 5rem;
	}
	a:nth-child(2n) {
		margin-top: 11rem;
	}
	a:nth-child(3n) {
		margin-top: 7rem;
	}
	a:last-of-type {
		margin-top: 4rem;
	}

	a.voor:nth-child(1n) {
		margin-top: 11rem;
	}
	a.voor:nth-child(2n) {
		margin-top: 6rem;
	}
	a.voor:nth-child(3n) {
		margin-top: 11rem;
	}

	@media only screen and (max-width: 700px) {
		a {
			width: 120%;
		}
	}
</style>
