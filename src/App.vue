<<template>
  <div class="box">
    <h3 class="title">App {{ movieId }}</h3>
    <Movie @chooseMovie="handleChooseMovie" :movieId="movieId" />
    <seat @chooseSeat="handleChooseSeat" :movieId="movieId" />
  </div>
  
  
  
  
</template>

<script>
  import Movie from './Movie.vue'
  import Seat from './Seat.vue'

  export default {
    components: { Movie , Seat },
    data() {
      return {
        movieId: '',
        selectSeats:[]
      }
    },
    methods: {
      handleChooseMovie(movieId){
        console.log(movieId)
        this.movieId = movieId
      },
      handleChooseSeat(seat){
        const ids = this.selectSeats.map(s => s.id)
        const idx = ids.indexOf(seat.id)
        if (idx === -1){
        this.selectSeats.push(seat)
        }
        
        console.log(ids)
      }
    }
  }
</script>
