<template lang="html">
  <div>

    <li v-on:click="handleClick" :class="">{{country.title}}
      <!-- <br><img v-on:click="handleClick" :src="findImg()"> -->
    </li>

    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'country-item',
  props: ['country'],
  data () {
    return {
      images: [
      { url: '../assets/SanFrancisco.jpeg', alt: 'San Francisco' },
      { url: '../assets/London.jpeg', alt: 'London' },
      { url: '../assets/Berlin.jpeg', alt: 'Berlin' },
      { url: '../assets/Moscow.jpeg', alt: 'Moscow' },
      { url: '../assets/Sydney.jpeg', alt: 'Sydney' }
    ]
    }
  },

  methods: {
    handleClick: function(){
      eventBus.$emit('country-selected', this.country);
    },

    findImg: function(){
      for (let image of this.images) {
        // debugger;
        if (image.alt == this.country.title) {
            return image.url
        }
      }
    }


  },
  computed: {
    // findImg: function(){
    //   debugger;
    //   for (let image in this.images) {
    //     if (image.alt == this.country.title) {
    //         return image.url
    //     }
    //   }
    // }
  }
}
</script>

<style lang="css" scoped>

/* li {
  float: left;
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
font-weight: bold;
  position: center;
  font-family: sans-serif;
  border-right: 1px solid #bbb;

} */

li {
  float: left;
  border-right:1px solid #bbb;
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-family: sans-serif;
  width: 130px;


}

li:hover:not(.active) {
  background-color: #111;
}

.active {
  background-color: #4CAF50;
}





</style>
