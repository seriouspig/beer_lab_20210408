<template>
  <section>
      <ul>
          <beer-item v-for="(beer, index) in beers" :beer="beer" :key="index"/>
      </ul>
  </section>
</template>

<script>
import BeerItem from './BeerItem.vue';

export default {
    name: 'beer-list',
    props: ['beers'],
    components : {
        "beer-item": BeerItem 
    },

   
    }



</script>

<style>
ul{
    list-style: none;
}
</style>