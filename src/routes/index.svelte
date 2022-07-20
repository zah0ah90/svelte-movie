<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=d5c35e51c81488b19da7c1f572507a3d&language=en-Us&page=1`
		);

		const data = await res.json();
		console.log(data);

		if (res.ok) {
			return {
				props: { popular: data.results }
			};
		}
	}
</script>

<script>
	import PopularMovie from '../components/PopularMovie.svelte';
	import SearchMovie from '../components/SearchMovie.svelte';
	import { fly } from 'svelte/transition';
	export let popular;

	// console.log(popular);
</script>

<section in:fly={{ duration: 500 }} out:fly={{ duration: 500 }}>
	<SearchMovie />
	<!-- <PopularMovie movie={popular} /> -->
	<PopularMovie {popular} />
</section>
