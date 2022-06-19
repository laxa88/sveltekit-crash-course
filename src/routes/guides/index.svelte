<script context="module" lang="ts">
	import type { LoadEvent } from '@sveltejs/kit';

	type Guide = {
		body: string;
		id: number;
		title: string;
		userId: number;
	};

	export async function load({ fetch }: LoadEvent) {
		const res = await fetch('https://jsonplaceholder.typicode.com/posts');
		const guides = await res.json();

		if (res.ok) {
			return {
				props: {
					hello: 'hello!',
					guides
				}
			};
		}

		return {
			status: res.status,
			error: new Error('Could not fetch guides')
		};
	}
</script>

<script lang="ts">
	export let guides: Guide[];
</script>

<div class="guides">
	<h2>Guides</h2>
	<ul>
		{#each guides as guide}
			<li><a href="/">{guide.title}</a></li>
		{/each}
	</ul>
</div>

<style>
	.guides {
		margin-top: 20px;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	a {
		display: inline-block;
		margin-top: 10px;
		padding: 10px;
		border: 1px dotted rgba(255, 255, 255, 0.2);
	}
</style>
