<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <Button
      is-primary
      @click="onClick"
      @mouseover="onMouseover"
    >
      Teste
    </Button>  
  </div>  
</template>

<script>
import Button from './components/Button/Button.vue'

export default {
  name: 'App',
  components: {
    Button,
  },

  methods: {
    onClick (e) {
      console.log('click: ', e)
    },

    onMouseover (e) {
      console.log('mouseover: ', e)
    },
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  img {
    border: 5px dotted red;
  }
}
</style>
