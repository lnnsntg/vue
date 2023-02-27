<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>
  <div>
    <button v-on:click="incrementarCounter">+ 1</button>
    <button @click="decrementarCounter">- 1</button>
  </div>
</template>

<script>

export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 25,
      required: true,
      validator(value) {
        return value > 100
      }
    }
  },

  name: 'Counter',

  data() {
    return {
      counter: this.start
    }
  },

  methods: {
    // Este metodo no se esta usando
    /*     getSquart () {
          console.log('0000')
          return Math.pow(this.counter, 2)
        }, */

    incrementarCounter() {
      return this.counter++
    },

    decrementarCounter() {
      return (this.counter = this.counter - 1)
    }
  },

  computed: {
    squareCounter() {
      // console.log('veces')
      return Math.pow(this.counter, 2)
    },

    customTitle() {
      return this.title || 'Counter'
      // return this.title ? this.title : 'Counter'
    }
  }
}
</script>

<style>
button {
  background-color: greenyellow;
  border-radius: 5px;
  border: 1px solid grey;
  color: darkolivegreen;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
}

button:hover {
  background-color: antiquewhite;
  transition: 0.6s ease-in-out;
}
</style>
