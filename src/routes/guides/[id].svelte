<script context="module" lang="ts">
	import type { LoadEvent, LoadOutput } from '@sveltejs/kit';
	import type { Guide } from './index.svelte';

	type PageParams = {
		id: string;
	};

	type PageProps = {
		guide: Guide;
	};

	export async function load({
		fetch,
		params
	}: LoadEvent<PageParams>): Promise<LoadOutput<PageProps>> {
		await new Promise((resolve) => setTimeout(resolve, 1000));
		const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
		const guide = await res.json();

		if (res.ok) {
			return {
				props: {
					guide
				}
			};
		}

		return {
			status: 301,
			redirect: '/guides'
		};
	}
</script>

<script lang="ts">
	export let guide: Guide;
</script>

<div class="guide">
	<h2>{guide.title}</h2>
	<p>{guide.body}</p>
</div>

<style>
	.guide {
		margin-top: 40px;
		padding: 10px;
		border: 1px dotted rgba(255, 255, 255, 0.2);
	}
</style>
