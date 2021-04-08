<template>
  <section>
      <li @click="handleClick">{{beer.name}}</li>
  </section>
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name: 'beer-item',
    props: ['beer'],
    methods: {
        handleClick() {
            eventBus.$emit('beer-selected', this.beer);
            console.log(this.beer.name)
        }
    }
}
</script>

<style>

</style>