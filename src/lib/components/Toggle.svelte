<script>
</script>

<section>
	<input type="checkbox" id="spooky-toggle" checked />
	<label for="spooky-toggle">
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
	--vampire-color: #4d7c99;
}

/* Styling van de toggle */
label {
	position: relative;
	display: flex;
	align-items: center;
	width: 5em;
	height: 1.5em;
	border: 2px solid var(--human-color);
	border-radius: 10rem;
	background: linear-gradient(to left, rgba(167, 129, 122, 0.9), rgba(219, 173, 165, 0.9));
	cursor: pointer;
	transition: 0.5s ease-in-out;
}

input:checked ~ label {
	border: 2px solid var(--vampire-color);
	background: linear-gradient(to right, rgba(133, 185, 218, 0.5), rgba(11, 105, 153, 0.9));
}

input ~ label::before,
input:checked ~ label::before {
	position: absolute;
	font-size: 1rem;
	text-transform: uppercase;
	transition: 0.5s ease;
}

input ~ label::before {
	left: 70%;
	color: var(--human-color);
	content: 'Light';
	transform: translateX(-70%);
}

input:checked ~ label::before {
	left: 25%;
	color: #a5d2ed;
	content: 'Dark';
	transform: translateX(-25%);
}

input ~ label .human-container,
input ~ label .vampire-container {
	position: absolute;
	left: 0.25rem;
	display: flex;
	justify-content: center;
	width: 0.95rem;
	height: 0.95rem;
	border-radius: 50%;
	overflow: hidden;
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
	left: -0.4rem;
}
.human-container::after,
.vampire-container::after {
	right: -0.4rem;
}

.human-eyes,
.vampire-eyes {
	position: absolute;
	top: 20%;
	z-index: 1;
}

.human-eyes::before,
.human-eyes::after {
	position: absolute;
	top: 0.1rem;
	left: 0;
	width: 0.1rem;
	height: 0.1rem;
	border-radius: 50%;
	background-color: rgb(61, 46, 35); /* eye-color */
	content: '';
}

.human-eyes::before,
.vampire-eyes::before {
	margin-left: -0.3rem;
}
.human-eyes::after,
.vampire-eyes::after {
	margin-left: 0.2rem;
}

.human-mouth,
.vampire-mouth {
	position: absolute;
	bottom: 10%;
	display: flex;
	justify-content: center;
	width: 0.7rem;
	height: 0.35rem;
	border-radius: 0 0 6.5rem 6.5rem;
	background-color: #330a0f;
	overflow: hidden;
	z-index: 1;
}

.human-teeth,
.vampire-teeth {
	position: absolute;
	top: -1px;
	width: 100%;
	height: 0.1rem;
	background-color: #fffae6; /* teeth-color */
	animation: smile 2s ease-in-out infinite;
}

.human-tongue,
.vampire-tongue {
	position: absolute;
	bottom: -0.2rem;
	width: 0.6rem;
	height: 0.3rem;
	border-radius: 3.5rem 3.5rem 0 0;
	background-color: #d63e49;
	animation: smile 3s ease-in-out infinite;
}

/* Styling van vampire karakter */
.vampire-container::before,
.vampire-container::after {
	position: absolute;
	top: 0.13rem;
	width: 100%;
	height: 100%;
	border-radius: 45% 45% 0 0;
	background-color: #c2def2; /* face color */
	content: '';
}

.vampire-eyes::before,
.vampire-eyes::after {
	position: absolute;
	top: 0.1rem;
	left: 0;
	width: 0.1rem;
	height: 0.1rem;
	border-radius: 50%;
	background-color: #d63e49; /* eye-color */
	content: '';
}

.vampire-teeth::before,
.vampire-teeth::after {
	position: absolute;
	top: 0.1rem;
	width: 0;
	height: 0;
	border-width: 0.07rem 0.0375rem 0 0.0375rem;
	border-style: solid;
	color: transparent;
	content: '';
	border-top-color: #fffae6;
}

.vampire-teeth::before {
	left: 0.1rem;
}
.vampire-teeth::after {
	right: 0.1rem;
}

/* Kleine mond animatie */
@keyframes smile {
	50% {
		transform: scaleY(1.5);
	}
}
</style>
