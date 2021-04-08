<template>
  <section>
      <h2>Favourite beers</h2>
        <ul>
            <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}}</li>
        </ul>
  </section>
</template>

<script>
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers']

}
</script>

<style scoped>

</style>