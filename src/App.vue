<template>
  <div>
    <headline></headline>
    <cards></cards>
  </div>
</template>

<script>
import Cards from './components/Cards.vue'
import Headline from './components/Headline.vue'

export default {
  name: 'App',
  components: {
    Cards,
    Headline
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;400;500;700&display=swap');

* {
  font-family: 'Ubuntu', sans-serif;
}

body {
  background: linear-gradient(180deg, rgba(86, 82, 244, 0.5) 0%, rgba(0, 255, 163, 0.11) 100%);
  height: 100vh;
}

#app {
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgba(54, 55, 60, 0.95);
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 24px;
}

</style>
