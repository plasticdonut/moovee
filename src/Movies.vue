<template>
  <div id="movies" class="">
    <div class="columns">
        <div v-for="movie in movies" v-bind:key="movie.title" class="column col-2">
          <movie-card v-bind:movie="movie"></movie-card>
        </div>
    </div>
  </div>
</template>
<script>
import MovieCard from './MovieCard.vue'

export default {
  name: 'movies',
  props: ['movies'],
  data () {
    return {
      api_key: 'api_key=7daac836cb57a577537d2d5ba0313dc8',
      search_type: 'now_playing',
      keywords: '',
      movie_api_url: 'https://api.themoviedb.org/3/movie/'
    }
  },
  created() {

  },
  components: {
    MovieCard
  },
  computed: {

  }, 
  methods: {
    open_link (link) {
      window.open(link);
    }
  }
}
</script>

<style lang="scss">
#topNav {
  margin-bottom: .8rem;
}
</style>
