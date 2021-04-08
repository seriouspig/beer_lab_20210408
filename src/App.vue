<template>
  <div id="app">
   <h1>Delicious BrewDog Beers</h1>
   <div class="main-container">
   <beer-list :beers="beers"/>  
   <beer-details :beer="selectedBeer" :favouriteBeers="favouriteBeers"></beer-details>
   </div>
    <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import BeerList from './components/BeerList.vue'
import BeerDetails from './components/BeerDetails.vue'
import FavouriteBeer from './components/FavouriteBeer.vue'



export default {
  name: 'App',
  data() {
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    }
  },
  components: {
    "beer-list": BeerList,
    "beer-details": BeerDetails,
    "favourite-beers": FavouriteBeer

    
    
  },
  async mounted() {
    const res = await fetch ('https://api.punkapi.com/v2/beers')
    const data = await res.json()
    this.beers = data

  // mounted() {
  //   fetch('https://api.punkapi.com/v2/beers')
  //   .then(res => res.json())
  //   .then(beers => this.beers = beers)

    this.beers.map(obj => obj.favourite = false)
    console.log(this.beers)

  eventBus.$on('beer-selected', (beer) => {
    this.selectedBeer = beer;
    })

  eventBus.$on('beer-added', (beer) => {
    this.selectedBeer = beer;
    
    this.favouriteBeers.push(beer)
    beer.favourite = true;
    console.log(this.favouriteBeers)
    })
  },
  methods: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.main-container {
  display: flex;
  justify-content:space-between;
}
</style>
