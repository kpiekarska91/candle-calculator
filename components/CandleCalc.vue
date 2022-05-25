<!-- Please remove this file from your project -->
<template>
  <div class="calculator-box">
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="weightCandle" class="calculator-box__input--label">Total weight (g)</label>
        <input @change="isNumber($event)" id="weightCandle" class="calculator-box__input--range" v-model="weightCandle" type="number">
      </div>
      <input @change="$emit('changeValue', weightCandle, percentageOil, numberOfCandles)" class="calculator-box__input-range" v-model="weightCandle"  type="range" min="0" max="1000">
    </div>
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="percentageOil" class="calculator-box__input--label">Oil fragrance (%)</label>
        <input @change="isNumber($event)" id="percentageOil" class="calculator-box__input--range" v-model="percentageOil" type="number">
      </div>
      <input @change="$emit('changeValue', weightCandle, percentageOil, numberOfCandles)" class="calculator-box__input-range" v-model="percentageOil"  type="range" min="0" max="20">
    </div>
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="numberOfCandles" class="calculator-box__input--label">Number Of Candles</label>
        <input @change="$emit('changeValue', weightCandle, percentageOil, numberOfCandles)" id="numberOfCandles" class="calculator-box__input--range" v-model="numberOfCandles" min="1" type="number">
      </div>
     </div>
  </div>
</template>

<script>
export default {
  name: 'CandleCalc',
  data () {
    return {
      weightCandle: 100,
      percentageOil: 10,
      numberOfCandles: 1,
    }
  },
  mounted () {
    this.$emit('changeValue', this.weightCandle, this.percentageOil, this.numberOfCandles)
  },
  methods: {
    isNumber: function(evt) {
      evt = (evt) ? evt : window.event;
      let charCode = (evt.which) ? evt.which : evt.keyCode
      if ((charCode > 31 && (charCode < 48 || charCode > 57)) && charCode !== 46) {
        evt.preventDefault();
      } else {
        this.$emit('changeValue', this.weightCandle,  this.percentageOil, this.numberOfCandles)
        return true;
      }
    }
  }
}
</script>

