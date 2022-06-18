<script>
	let title = 'Ninja Gaming Guides';

	const setTitle = () => {
		title = 'something completely different';
	};
</script>

<div class="index">
	<h2>{title}</h2>
	<p>Lorem ipsum dolor sit amet</p>

	<button on:click={setTitle}>Change tile</button>
	<input type="text" bind:value={title} />
</div>

<style>
	.index {
		text-align: center;
		display: block;
		margin: 20px auto;
	}
</style>
