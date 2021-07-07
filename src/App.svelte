<script>
	import AddBlog from './AddBlog.svelte'
	import Blogs from './Blogs.svelte'
</script>

<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css">
	<link href="https://fonts.googleapis.com/css?family=Play" rel="stylesheet">
</svelte:head>
<main>
	<AddBlog />
	<Blogs />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>