<script context="module">
	export async function load({ fetch, params }) {
		const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${params.slug}`);
		return {
			props: {
				post: response.ok && (await response.json())
			}
		};
	}
</script>

<script>
	export let post;
</script>

<div class="post">
	<h2>{post.title}</h2>
	<p>{post.body}</p>
</div>

<style>
	.post {
		padding: 10px;
	}
</style>
