<script>
	import Title from '$lib/title.svelte';

	let title = 'Ninja Gaming Guides';

	const setTitle = () => {
		title = 'something completely different';
	};
</script>

<div class="index">
	<Title>{title}</Title>
	<p>
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat eaque debitis excepturi impedit
		et, perspiciatis optio dolorem similique exercitationem beatae voluptas, quisquam deserunt natus
		nam repellat id quam at iure!
	</p>

	<button on:click={setTitle}>Change title</button>
	<input type="text" bind:value={title} />

	<p />

	<a href="/guides">View Guides</a>
	<a href="/about">About</a>
</div>

<style>
	.index {
		text-align: center;
		display: block;
		margin: 20px auto;
	}
</style>
