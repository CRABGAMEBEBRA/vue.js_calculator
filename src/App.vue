<template>
  <div id="app">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
@import url(http://fonts.googleapis.com/css?family=Oswald:700|Orbitron);

body {
  background: #71B66F;
  box-sizing: border-box;
  margin: 0;
  padding: 20px;
  width: 100%;
}
</style>
