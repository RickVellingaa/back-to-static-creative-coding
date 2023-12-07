<script>
	import Heading from '$lib/components/heading.svelte';
	$: heading = { titel: 'Toggle' };
</script>

<Heading {heading} />

<section>
	<input type="checkbox" id="spooky-toggle-groot" checked />
	<label for="spooky-toggle-groot">
		<div class="human-container">
			<div class="human-eyes" />
			<div class="human-mouth">
				<div class="human-teeth" />
				<div class="human-tongue" />
			</div>
		</div>
		<div class="vampire-container">
			<div class="vampire-eyes" />
			<div class="vampire-mouth">
				<div class="vampire-teeth" />
				<div class="vampire-tongue" />
			</div>
		</div>
	</label>
</section>

<style>
	@import url('https://fonts.googleapis.com/css?family=Kodchasan');

	:root {
		--human-color: #ecbcb4;
		--vampire-color: #5a8097;
	}

	section {
		display: flex;
		align-items: center;
		justify-content: center;
		overflow: hidden;
		height: calc(100vh - 321px);
		width: 100%;
	}

	/* Styling van de toggle */
	label {
		height: 10em;
		width: 30em;
		border: 5px solid var(--human-color);
		border-radius: 10rem;
		background: linear-gradient(to left, rgba(167, 129, 122, 0.9), rgba(219, 173, 165, 0.9));
		cursor: pointer;
		display: flex;
		align-items: center;
		position: relative;
		transition: 0.5s ease-in-out;
	}

	input:checked ~ label {
		border: 5px solid var(--vampire-color);
		background: linear-gradient(to right, rgba(133, 185, 218, 0.5), rgba(11, 105, 153, 0.9));
	}

	input ~ label::before,
	input:checked ~ label::before {
		position: absolute;
		font-size: 2.5rem;
		text-transform: uppercase;
		transition: 0.5s ease;
	}

	input ~ label::before {
		content: 'Light';
		color: var(--human-color);
		left: 70%;
		transform: translateX(-70%);
	}

	input:checked ~ label::before {
		content: 'Dark';
		color: #a5d2ed;
		left: 25%;
		transform: translateX(-25%);
	}

	input ~ label .human-container,
	input ~ label .vampire-container {
		width: 9.5rem;
		height: 9.5rem;
		border-radius: 50%;
		position: absolute;
		left: 0.25rem;
		overflow: hidden;
		display: flex;
		justify-content: center;
		transition: 0.5s ease;
	}

	input ~ label .human-container {
		background-color: var(--human-color);
		filter: opacity(1);
	}

	input ~ label .vampire-container {
		background-color: var(--vampire-color);
		filter: opacity(0);
	}

	input:checked ~ label .human-container {
		left: calc(100% - 0.25rem);
		transform: translateX(-100%);
		filter: opacity(0);
	}

	input:checked ~ label .vampire-container {
		left: calc(100% - 0.25rem);
		transform: translateX(-100%);
		filter: opacity(1);
	}

	input {
		display: none;
	}

	/* Styling van de karakters */
	.human-container::before,
	.vampire-container::before {
		left: -4rem;
	}
	.human-container::after,
	.vampire-container::after {
		right: -4rem;
	}

	.human-eyes,
	.vampire-eyes {
		top: 20%;
		position: absolute;
		z-index: 1;
	}

	.human-eyes::before,
	.human-eyes::after {
		content: '';
		position: absolute;
		width: 1rem;
		height: 1rem;
		background-color: rgb(61, 46, 35); /* eye-color */
		border-radius: 50%;
		top: 0.5rem;
		left: 0;
	}

	.human-eyes::before,
	.vampire-eyes::before {
		margin-left: -3.25rem;
	}
	.human-eyes::after,
	.vampire-eyes::after {
		margin-left: 2.25rem;
	}

	.human-mouth,
	.vampire-mouth {
		position: absolute;
		width: 6.5rem;
		height: 3.25rem;
		background-color: #330a0f;
		bottom: 10%;
		border-radius: 0 0 6.5rem 6.5rem;
		display: flex;
		justify-content: center;
		overflow: hidden;
		z-index: 1;
	}

	.human-teeth,
	.vampire-teeth {
		position: absolute;
		width: 100%;
		height: 1rem;
		background-color: #fffae6; /* teeth-color */
		top: -1px;
		animation: smile 2s ease-in-out infinite;
	}

	.human-tongue,
	.vampire-tongue {
		position: absolute;
		width: 3.5rem;
		height: 1.75rem;
		background-color: #d63e49;
		bottom: -0.75rem;
		border-radius: 3.5rem 3.5rem 0 0;
		animation: s-IxVFScgfBrOo-smile 3s ease-in-out infinite;
	}

	/* Styling van vampire karakter */
	.vampire-container::before,
	.vampire-container::after {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background-color: #c2def2; /* face color */
		border-radius: 45% 45% 0 0;
		top: 0.75rem;
	}

	.vampire-eyes::before,
	.vampire-eyes::after {
		content: '';
		position: absolute;
		width: 1rem;
		height: 1rem;
		background-color: #d63e49; /* eye-color */
		border-radius: 50%;
		top: 0.5rem;
		left: 0;
	}

	.vampire-teeth::before,
	.vampire-teeth::after {
		content: '';
		position: absolute;
		width: 0;
		height: 0;
		color: transparent;
		border-style: solid;
		border-width: 0.65rem 0.375rem 0 0.375rem;
		border-top-color: #fffae6;
		top: 0.95rem;
	}

	.vampire-teeth::before {
		left: 1rem;
	}
	.vampire-teeth::after {
		right: 1rem;
	}

	/* Kleine mond animatie */
	@keyframes smile {
		50% {
			transform: scaleY(1.5);
		}
	}
</style>
