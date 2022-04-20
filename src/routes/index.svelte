<script context="module">
	export async function load({ fetch }) {
		const response = await fetch('https://jsonplaceholder.typicode.com/posts');
		return {
			props: {
				posts: response.ok && (await response.json())
			}
		};
	}
</script>

<script>
	export let posts;
</script>

<ul class="post-list">
	{#each posts as post}
		<li><a href={`posts/${post.id}`} class="post-link">{post.title}</a></li>
	{/each}
</ul>

<style>
	.post-list {
		list-style-type: decimal;
	}

	.post-list > li {
		margin-top: 10px;
	}

	.post-link {
		color: #000;
		text-decoration: none;
	}

	.post-link:hover {
		text-decoration: underline;
	}
</style>
