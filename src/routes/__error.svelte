<script context="module" lang="ts">
	import type { LoadEvent, LoadOutput } from '@sveltejs/kit';

	type PageProps = {
		message?: string;
	};

	export function load({ error, status }: LoadEvent): LoadOutput<PageProps> {
		return {
			props: { message: error?.message }
		};
	}
</script>

<script lang="ts">
	export let message: string;
</script>

<div class="error">
	<h2>Ooops</h2>
	<p>{message}</p>
	<a href="/guides">View all guides...</a>
</div>

<style>
	.error {
		text-align: center;
		margin-bottom: 60px;
	}
</style>
