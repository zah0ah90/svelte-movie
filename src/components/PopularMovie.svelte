<script>
	export let popular;
	console.log(popular[0]);
	import MovieCard from './MovieCard.svelte';
</script>

<h3>Popular Movies</h3>
<div class="popular-movies">
	{#each popular as movie}
		<!-- <h1>{movie.title}</h1> -->
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h3 {
		padding: 0 1 rem;
	}

	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
	}
</style>
