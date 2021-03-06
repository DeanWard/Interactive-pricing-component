<template>
  <div :id="'pricing-card-' + _uid" class="pricing-card">
    <div class="pricing-row">
      <div class="pageviews" v-if="value !== 1000">{{value}}K Pageviews</div>
      <div class="pageviews" v-else>1M Pageviews</div>
      <div class="price">${{price}}.00 <span>/ month</span></div>
    </div>
    <div style="padding: 0 10% 0 10%;">
      
    
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
    :min="10"
    :max="1000"
    :step="10"
    ></vue-range-slider>
    </div>
    <div class="period-select">
      <div>Monthly Billing</div>
      <div class="toggle">
        <input type="checkbox" id="toggle" name="toggle" v-model="yearly">
        <label for="toggle"></label>
      </div>
      <div class="yearly">Yearly Billing <span>25% discount</span></div>
    </div>

    <footer>
      <ul>
        <li>Unlimited websites</li>
        <li>100% data ownership</li>
        <li>Email reports</li>
      </ul>
      <div class="cta">Start my trial</div>
    </footer>
</div>
</template>
<script>
  import 'vue-range-component/dist/vue-range-slider.css'
  import VueRangeSlider from 'vue-range-component'
  export default {
    data() {
      return {
        yearly: false,
        value: 100,
        sliderStyle: {
          backgroundColor: 'hsl(174, 86%, 45%)',
          height: '40px',
          width: '40px',
          marginTop: '-12px',
          boxShadow: '0 20px 20px 10px hsl(174, 86%, 45%, 20%)'
        }
      }
    },
    created() {
      VueRangeSlider.methods.handleKeyup = ()=> console.log
      VueRangeSlider.methods.handleKeydown = ()=> console.log
    },
    components: {
      VueRangeSlider
    },
    computed: {
      price() {
        var price
        if(this.value < 50) {
          price = 8
        }
        if(this.value >= 50) {
          price = 12
        }
        if(this.value >= 100) {
          price = 16
        }
        if(this.value >= 500) {
          price = 24
        }
        if(this.value >= 1000) {
          price = 36
        }

        if(this.yearly) {
          price = price - (price * 0.25)
        }
        return price
      }
    }
  }
</script>
<style lang="scss">
@import '../scss/_vars';
.pricing-card {
  z-index: 1;
  position: relative;
  background: #fff;
  min-height: 46vh;
  width: 38vw;
  border-radius: 10px;
  margin: auto;
  box-shadow: 0px 0px 15px 0px rgba(0,0,0,0.05);
}
.pricing-row {
  display: flex;
  flex-direction:row;
  justify-content:space-between;
  align-items:center;
  color: $gray-blue;
  margin-bottom: 6.3%;
  padding: 7% 10% 0 10%;
}

.price {
  font-weight: 800;
  font-size: 2.6em;
  color: $dark-blue;
  display: flex;
  flex-direction:row;
  justify-content:space-between;
  align-items:center;
  span {
    font-size: 0.4em;
    font-weight: 600;
    color: $gray-blue;
    padding-left: 3%;
    white-space: nowrap;
  }
}

.pageviews {
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-weight: 600;
}
.slider-dot {
  background-image: url(../assets/icon-slider.svg)!important;
  background-repeat: no-repeat;
  background-position: center;
}
.period-select {
  margin-top: 3.5em;
  display: flex;
  flex-direction:row;
  justify-content:center;
  align-items:center;
  color: $gray-blue;
  font-weight: 600;
  font-size: 0.8em;
  letter-spacing: 0.05em;
  padding: 0 10% 0 10%;
}

.yearly {
  span {
    background: $light-gray-red;
    color: $light-red;
    margin-left:5px;
    padding: 1px;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 10px;
  }
}
.toggle {
  input {
    transform: translateX(-200vw);
    width: 0px;
  }
  label {
    margin-right: 15px;
    margin-left: 5px;
    transform: translateY(4px);
    display: inline-block;
    background: $light-gray-blue-2;
    width: 50px;
    height: 21px;
    border-radius: 10px;
    position: relative;
    cursor: pointer;
    &:hover {
      background: $soft-cyan;
    }
    &:after {
      position: absolute;
      content: "";
      width: 15px;
      height: 15px;
      background: white;
      border-radius: 100%;
      top:3px;
      left: 4px;
      transition: all 250ms ease-in-out;
    }
  }
  input:checked + label {

    &:after {
      position: absolute;
      content: "";
      width: 15px;
      height: 15px;
      background: white;
      border-radius: 100%;
      top:3px;
      left: 31px;
      transition: all 250ms ease-in-out;
    }
  }
}

footer {
  margin-top: 8%;
  border-top: 1px solid $light-gray-blue-1;
  padding-top: 8%;
  display: flex;
  flex-direction:row;
  justify-content:space-between;
  align-items:center;
  color: $gray-blue;
  font-weight: 600;
  font-size: 0.8em;
  letter-spacing: 0.05em;
  padding: 5% 10% 5% 10%;

  .cta {
    background: $dark-blue;
    color: $pale-blue;
    padding: 3% 9%;
    border-radius: 20px;
    cursor: pointer;
    &:hover {
      color:white;
    }
  }

  ul {
    padding: 0px;
    margin: 0px;
    li {
      line-height: 2em;
      list-style: none;
      &:before {
        content: "";
        background: url('../assets/icon-check.svg') no-repeat center;
        width: 20px;
        height: 10px;
        display: inline-block;
        margin-right: 10px;
      }
    }
  }
}
</style>