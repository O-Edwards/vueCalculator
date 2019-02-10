<template>
  <section class="container">
    <Calculator />
  </section>
</template>

<script>
import Calculator from '../components/Calculator.vue'
export default {
  components: { Calculator }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
  background-color: black;
}
</style>
