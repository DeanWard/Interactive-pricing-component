<template>
  <div>
   <vue-range-slider
    ref="slider"
    v-model="value"
    :bg-style="{
      backgroundColor: 'hsl(224, 65%, 95%)',
      height: '8px'
    }"
    :process-style="{
      backgroundColor: 'hsl(174, 77%, 80%)'
    }"
    :slider-style="sliderStyle"
    :tooltip="false"
    ></vue-range-slider>
  </div>
</template>

<script>
  import 'vue-range-component/dist/vue-range-slider.css'
  import VueRangeSlider from 'vue-range-component'

  export default {
    data() {
      return {
        value: 0,
        sliderStyle: {
          backgroundColor: 'hsl(174, 86%, 45%)',
          height: '40px',
          width: '40px',
          marginTop: '-12px',
          boxShadow: '0 20px 20px 10px hsl(174, 86%, 45%, 20%)'
        }
      }
    },
    components: {
      VueRangeSlider
    }
  }
</script>

<style lang="scss">
  .slider-dot {
    background-image: url(../assets/icon-slider.svg)!important;
    background-repeat: no-repeat;
    background-position: center;
  }
</style>