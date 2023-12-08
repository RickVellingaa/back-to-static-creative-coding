<script context="module">
	let js = true;
</script>

<script>
	// https://kit.svelte.dev/docs/assets
	import logo from '$lib/assets/vervoerregio_amsterdam_logo.svg';
	import informationIcon from '$lib/assets/information_icon.svg';
	import darkmodeIcon from '$lib/assets/dark_mode_icon.svg';

	import { onMount } from 'svelte';
	import Toggle from './Toggle.svelte';

	export let params;
	export let partners;
	export let websites;

	const faviconAPI =
		'https://t1.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=';

	$: selectedPartner = params.websiteUID
		? partners.websites.find(({ slug }) => slug === params.websiteUID)
		: '';
	$: selectedUrl = params.urlUID ? params.urlUID : '';
	let js = false;

	onMount(() => {
		js = true;
	});
</script>

<header>
	<nav>
		<section class="logo-select">
			<a href="/">
				<img src={logo} alt="logo vervoerregio" />
			</a>
			<div class="dropdown">
				<button>
					{#if selectedPartner}
						<img
							width="24"
							src="{faviconAPI}{selectedPartner.homepage}/&size=128"
							alt=""
						/>{selectedPartner.titel}
					{:else}
						<span>Partners overzicht</span>
					{/if}
				</button>
				<ul>
					<li>
						<a href="/">Partners overzicht</a>
					</li>
					{#each partners.websites as partner}
						<li>
							<a href="/{partner.slug}"
								><img
									width="24"
									src="{faviconAPI}{partner.homepage}/&size=256"
									alt=""
								/>{partner.titel}</a
							>
						</li>
					{/each}
				</ul>
			</div>

			{#if websites}
				<span class="seperator">/</span>
				<div class="dropdown">
					<button>
						{#if selectedUrl}
							{selectedUrl}
						{:else}
							<span>Websites overzicht</span>
						{/if}
					</button>
					<ul>
						<li>
							<a href="/{selectedPartner.slug}">Websites overzicht</a>
						</li>
						{#each websites.urls as website}
							<li>
								<a href="/{selectedPartner.slug}/{website.slug}">{website.slug}</a>
							</li>
						{/each}
					</ul>
				</div>
			{/if}
		</section>

		<section class="header-icons">
			<a href="/info">
				<img class="information-icon-img" src={informationIcon} alt="information icon" />
			</a>
			<!-- <img src={darkmodeIcon} alt="darkmode icon" /> -->
			<Toggle />
		</section>
	</nav>
</header>

<style>
	header {
    position: sticky;
    top: 0;
    display: flex;
    flex-direction: column;
}

nav {
    display: flex;
    justify-content: space-between;
    background-color: #202020;
    padding: 1em;
    border-bottom: 2px solid #454545;
}

.seperator {
    font-size: 1.5rem;
}

button {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    height: 3.5rem;
    border: none;
    border-radius: 0.5em;
    color: #ffffff;
    background-color: #2c2c2c;
    font-size: 1em;
    text-align: left;
    gap: 0.5rem;
    appearance: none;
    padding: 1em 0.6em;
    padding-right: 4em;
    box-shadow: 0px -20px 0px 0px #202020;
    transition: 0.2s;
}

button::after {
    position: absolute;
    right: 5%;
    content: url('../assets/select_arrow_down.svg');
    scale: 1.3;
    transition: 0.2s;
}

button span {
    opacity: 0.6;
}

.dropdown {
    position: relative;
    display: inline-block;
    height: max-content;
    min-width: 19rem;
    z-index: 1;
}

.dropdown img {
    width: 24px;
    height: 24px;
    border-radius: 4px;
}

ul {
    position: absolute;
    width: 100%;
    border-radius: 0 0 0.5em 0.5em;
    background-color: #2c2c2c;
    max-height: 0;
    overflow: hidden;
    transform: translateY(-100%);
    transition: 0.2s;
    z-index: -1;
}

ul li:first-child {
    border-bottom: 1px solid;
}

ul a {
    display: flex;
    display: block;
    align-items: center;
    color: #ffffff;
    background-color: #393939;
    gap: 0.5rem;
    padding: 12px 16px;
    text-decoration: none;
}

ul:has(a:focus) {
    max-height: min-content;
    min-width: max-content;
    transform: translateY(0);
}

ul a:hover {
    background-color: #525252;
}

ul a:hover img {
    transform: translateY(-3px);
}

.dropdown:hover ul {
    max-height: min-content;
    min-width: max-content;
    transform: translateY(0);
}

.dropdown:hover button {
    border-radius: 0.5em 0.5em 0 0;
    background-color: #2c2c2c;
}

button:has(a:focus) {
    border-radius: 0.5em 0.5em 0 0;
    background-color: #2c2c2c;
}

.dropdown:hover button::after {
    transform: scale(-1, -1);
}

.logo-select {
    display: flex;
    align-items: center;
    gap: 0.5em;
}

.logo-select a {
    display: flex;
}

.header-icons {
    display: flex;
    align-items: center;
    gap: 1em;
}

.information-icon-img {
    display: block;
}
</style>
