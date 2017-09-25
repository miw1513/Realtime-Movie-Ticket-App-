<template>
    <div class="box">
           <template v-for="s in seats">
               <button 
               :class="className(s)"
               :disabled="s.seated"
               @click="chooseSeat(s)"
               >{{ s.id}} {{s.price}} </button>
               <span>&nbsp;</span>
               </template>
            
    </div>
</template>

<script>
import movie from './movie.json'

    export default {

        props: [ 'movieId' ],
        methods: {
            className(seat){
                return [
                    'button' , { 'is-danger': seat.seated}
                ]
            },
            chooseSeat(seat){
                this.$emit('chooseSeat',seat)
            }
        },
        computed: {
            seats(){
                
               return movie[this.movieId]
            }
        }

    }
</script>