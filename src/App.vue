<template>
  <div id="app">

    <div class="container grid" id="app">
      <div class="columns">
        <div class="column col-2">
          <side-nav v-on:changeType="changeType"></side-nav>
        </div>
        <div class="column col-9">
          <movies v-bind:movies="movies"></movies>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SideNav from './SideNav.vue'
import Movies  from './Movies.vue'
var axios = require('axios')

export default {
  name: 'app',
  data () {
    return {
      api_key: 'api_key=7daac836cb57a577537d2d5ba0313dc8',
      search_type: 'now_playing',
      movie_api_url: 'https://api.themoviedb.org/3/movie/',
      movies: [],
      search: '',
      keywords: '',
      search_type: 'now_playing'
    }
  },
  created: function() {
     this.request_movies()
  },
  components: {
    SideNav,
    Movies
  },
  computed: {

  }, 
  methods: {
    open_link (link) {
      window.open(link);
    },
    changeType(new_type) {
      console.log('changing type')
      console.log(new_type)
      this.search_type = new_type
      this.request_movies()
    },
    request_movies() {    
      var self = this
      axios.get(self.movie_api_url + self.search_type + '?' +self.api_key + "&query=" + self.keywords)
        .then(function (response) {
          console.log(response)
          self.movies = response.data.results
        })
        .catch(function (error) {
          console.log(error)
        });
    }
  }
}
</script>

<style lang="scss">
  body {
    margin-top: 1.6rem
  }

</style>
