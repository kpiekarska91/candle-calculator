<!-- Please remove this file from your project -->
<template>
  <div class="calculator-box">
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="weightCandle" class="calculator-box__input--label">Wax (g)</label>
        <input id="weightCandle" class="calculator-box__input--range" v-model="weightCandle" type="number">
      </div>
      <input class="calculator-box__input-range" v-model="weightCandle"  type="range" min="0" max="1000">
    </div>
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="percentageOil" class="calculator-box__input--label">Fragrance (%)</label>
        <input id="percentageOil" class="calculator-box__input--range" v-model="percentageOil" type="number">
      </div>
      <input class="calculator-box__input-range" v-model="percentageOil"  type="range" min="0" max="20">
    </div>
    <div class="calculator-box__input">
      <div class="calculator-box__input--group-top">
        <label for="numberOfCandles" class="calculator-box__input--label">Number Of Candles</label>
        <input id="numberOfCandles" class="calculator-box__input--range" v-model="numberOfCandles" min="1" type="number">
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
      percentageOil: 100,
      numberOfCandles: 1,
    }
  }
}
</script>

