<script context="module">
	export async function load({ fetch, params }) {
		console.log(params.id);
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=d5c35e51c81488b19da7c1f572507a3d&language=en-Us&page=1`
		);

		const movieDetail = await res.json();
		console.log(movieDetail);

		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	// export let movie;
	export let movieDetail;
	console.log(movieDetail);
</script>

<div class="movie-detail">
	<div class="img-container">
		<img
			src={`https://image.tmdb.org/t/p/original` + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>

	<div class="txt-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">{movieDetail.overview}</p>
		<p>
			<span>Release Date: </span>
			{movieDetail.release_date} <br />
			<span>Budget: </span>
			{movieDetail.budget} <br />
			<span>Rating: </span>
			{movieDetail.vote_average} <br />
			<span>Runtime: </span>
			{movieDetail.runtime} mins
		</p>
	</div>
</div>

<style>
	h1 {
		padding: 1rem 0rem 2rem;
	}
	p {
		padding: 1rem 0rem;
	}
	.img-container {
		width: 100%;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		margin: 2rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>
