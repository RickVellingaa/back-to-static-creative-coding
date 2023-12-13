<script>
	export let data;
</script>

<section>
	<div>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
	</div>
	<div>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
		<ul>
			<li>
				<a href="">
					<figure>
						<figcaption>1</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>2</figcaption>
					</figure>
				</a>
			</li>
			<li>
				<a href="">
					<figure>
						<figcaption>3</figcaption>
					</figure>
				</a>
			</li>
		</ul>
	</div>
</section>

<style>
	* {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}
	section {
		position: relative;
		width: 1680px;
		margin-left: auto;
		margin-right: auto;
		height: calc(100vh - 90px);
	}

	div {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		grid-gap: 0 10rem, 0.5rem;
		gap: 0 10rem, 0.5rem;
		width: 100%;
		height: 100%;
		padding: 0em 1.5em;
	}

	ul {
		height: 100%;
		width: 100%;
		list-style: none;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
		gap: 1em;
		padding: 0 2em;
	}

	li {
		width: 100%;
		aspect-ratio: 2.5/1;
		background-color: red;
	}

	a {
		color: white;
		text-decoration: none;
	}

	/* Background containers */

	section > div:nth-child(2) {
		position: absolute;
		left: 0;
		top: 0;
	}
</style>
