<template>
    <div class="card">
        <div class="card-image">
            <img :src="this.poster_url" class="img-responsive">
        </div>
        <div class="card-header">
            <div class="card-title h5">{{ movie.original_title }} <small>{{rating}}</small></div>
        </div>
        <div class="card-body">
            <p class="ellipsis">
            {{ this.movie.overview }}
            </p>
        </div>
    </div>
</template>
<script>
var axios = require('axios')
export default {
  props: ['movie'],
  data () {
    return {

    }
  },
  computed: {
      poster_url: function() {
          return 'https://image.tmdb.org/t/p/w300_and_h450_bestv2/' + this.movie.poster_path
      },
      rating: function() {
          var score = parseFloat(this.movie.vote_average)
          var out_of_5 = (score / 2).toFixed(1) + '/5'
          if(score > 7.5) {
              return '🔥  ' + out_of_5
          }
          if(score > 8) {
              return '🔥🔥  ' + out_of_5
          }
          if(score > 9) {
              return '🔥🔥🔥  ' + out_of_5
          }
          return out_of_5
      },
      short_overview: function() {
          return this.movie.overview.substring(0,200) + '...'
      }
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
.card {
    margin-bottom: 1.2rem;
    .card-body {
        padding-top: .4rem;
    }
    .card-title.h5 {
        font-size: .8rem;
        min-height: 2rem;
        small {
            float: right;
        }
    }
}
.ellipsis {
   overflow: hidden;
   text-overflow: ellipsis;
   display: -webkit-box;
   -webkit-box-orient: vertical;
   -webkit-line-clamp: 4; /* number of lines to show */
   min-height: 4*1.2rem;       /* fallback */
   line-height: 1.2rem;        /* fallback */
   max-height: 4*1.2rem;       /* fallback */
}
</style>
