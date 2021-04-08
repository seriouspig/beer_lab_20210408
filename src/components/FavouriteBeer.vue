<template>
  <section>
      <h2>Favourite beers</h2>
        <ul>
            <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}}
                <button @click="removeFromFavourites">Remove from Favourites</button>
            </li>
        </ul>
  </section>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: 'favourite-beers',
    props: ['favouriteBeers', 'beer'],
    methods: {
        removeFromFavourites() {
             eventBus.$emit('beer-removed', this.beer);
        }
    }


}
</script>

<style scoped>

</style>