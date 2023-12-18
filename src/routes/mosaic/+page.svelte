<script>
	import { gsap } from 'gsap/dist/gsap';
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
	import noise from '$lib/assets/noise.png';

	import { onMount } from 'svelte';

	import Mosaic from '$lib/components/Mosaic.svelte';
	export let data;
	gsap.registerPlugin(ScrollTrigger);

	onMount(() => {
		let tl = gsap.timeline({
			scrollTrigger: {
				trigger: 'ul.bg',
				start: `-10% top`,
				end: `200% bottom`,
				scrub: 1,
				markers: false
			}
		});
		tl.to('ul.bg', {
			y: 900
		});
	});
</script>

<section style="background-image: url({noise});">
	<ul>
		{#each data.websites as website}
			<Mosaic {website} layer="voor" />
		{/each}
	</ul>

	<ul class="bg">
		{#each data.websites.reverse() as website}
			<Mosaic {website} layer="achter" />
		{/each}
	</ul>

	<div class="circle" style="background-image: url({noise});">
		<span />
		<span />
		<span />
	</div>
</section>

<style>
	* {
		box-sizing: border-box;
	}

	section {
		position: relative;
		height: calc(220vh - 92px);
		width: 100%;
		max-width: 100vw;
		margin: 0 auto 10rem auto;
		overflow-y: hidden;
		overflow: hidden;
	}

	ul {
		position: absolute;
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		column-gap: 5%;
		width: 100%;
		/* top: 0; */
		left: 50%;
		/* transform: translateX(-50%); */
		margin-left: -50%;
		overflow: hidden;
		padding: 0 10em;
		padding-bottom: 5em;
	}

	ul.bg {
		/* top: -20rem; */
		column-gap: 3%;
		/* z-index: -1; */
		opacity: 0.8;
		outline: none;
		/* pointer-events: none; */
	}

	@media only screen and (max-width: 700px) {
		ul {
			grid-template-columns: repeat(2, 1fr);
		}
	}
</style>
