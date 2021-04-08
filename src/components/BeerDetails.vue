<template>
  <section v-if='beer'>
      <h3>{{beer.name}}</h3>
      <img :src="beer.image_url" alt="beer_photo">
      <p>{{beer.tagline}}</p>
      <p>{{beer.abv}}% Alcohol</p>
      <p>Favourite beer: {{beer.favourite}}</p>
      <button v-if="!favouriteBeers.includes(beer)" @click="addToFavourites">Add to Favourites</button>
      


  </section>
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name: 'beer-detail', 
    props: ['beer', 'favouriteBeers'],
    methods: {
        addToFavourites() {
            eventBus.$emit('beer-added', this.beer);
        }
    }
    

}
</script>

<style scoped>
img {
    height: 100px;
}
</style>