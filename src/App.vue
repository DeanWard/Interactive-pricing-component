<template>
  <div id="app">

  <div id="header">
    <h1>Simple, traffic-based pricing</h1>
    <p>Sign-up for our 30-day trial. No credit card required. </p>
  </div>
  <pricingCard />
  </div>
</template>

<script>
import pricingCard from './components/pricing-card.vue'

export default {
  name: 'App',
  components: {
    pricingCard
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600;800&display=swap');
  @import './scss/_reset';
  @import './scss/_vars';

  #app {
    font-family: 'Manrope', sans-serif;
    font-size: 15px;
    background: $very-pale-blue;
    width: 100vw;
    height: 100vh;
  }

  #header {
    background: $pale-gray-blue;
    background-image: url(./assets/pattern-circles.svg);
    background-repeat: no-repeat;
    background-position: center 28%;
    display: flex;
    padding-top: 14vh;
    flex-direction:column;
    justify-content:flex-start;
    align-items:center;
    height:54vh;
    border-radius:0% 0% 0% 20% / 0% 0% 0% 40%;
    margin-bottom: -11.65%;
    z-index: -1;
    h1 {
      color: $dark-blue;
      font-weight: 800;
      margin-bottom: 0.25em;
      font-size: 1.7em;
      letter-spacing: 0.02em;
    } 
    p {
      color: $gray-blue;
      font-weight: 600;
    }
  }

</style>
