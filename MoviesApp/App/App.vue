<template>
	<div>
		<div class="row">
			<div class="col-sm-4" v-for="movie in movies" v-bind:key="movie.id">
				<div class="card mt-3">
					<div class="card-body">
						<h4 class="card-title">{{movie.title}}</h4>
						<h6 class="card-subtitle mb-2 text-muted">{{movie.year}} - {{movie.director}}</h6>
						<p class="card-text">
							{{movie.description}}
						</p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	import axios from 'axios'
	export default {
		name: 'app',
		data() {
			return {
				movies: []
			};
		},
		mounted() {
			this.getMovies();
		},
		methods: {
			getMovies() {
				axios({
					method: 'GET', 'url': '/api/movies'
				}).then(result => {
					this.movies = result.data;
				}, error => {
					console.error(error);
				});
			}
		}
	}
</script>
<style lang="scss">
</style>
