<!-- Please remove this file from your project -->
<template>
  <div class="calculator-box">
    <div class="calculator-box__summary">
      <p class="calculator-box__summary--title">Wax (g)</p>
      <p class="calculator-box__summary--sum">{{ weightWax }}g</p>
    </div>
    <div class="calculator-box__summary">
      <p class="calculator-box__summary--title">Oil fragrance (g)</p>
      <p class="calculator-box__summary--sum">{{ weightOil }}g</p>
    </div>
    <div class="calculator-box__summary calculator-box__summary--right">
      <button :disabled="weightWax == 0 || weightOil == 0" @click="copyLink" class="calculator-box__summary--button" type="button">Copy</button>
      <div :class="showTooltip ? 'tooltip-info-copy tooltip-info-copy-show' : 'tooltip-info-copy'">copied</div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'CandleCalc',
  data () {
    return {
      weightWax: 0,
      weightOil: 0,
      showTooltip: false
    }
  },
  props: {
    weightCandle: Number,
    percentageOil: Number,
    numberOfCandles: Number,
  },
  watch: {
    weightCandle () {
      this.calculateConcentration()
    },
    percentageOil () {
      this.calculateConcentration()
    },
    numberOfCandles () {
      this.calculateConcentration()
    }
  },

  mounted () {
    this.calculateConcentration()
  },
  methods: {
    calculateConcentration () {

      if (this.weightCandle && this.percentageOil && this.numberOfCandles) {
        let weightWaxNetto = this.weightCandle / (1 + (this.percentageOil / 100))

        this.weightWax = (weightWaxNetto * this.numberOfCandles).toFixed(1)
        this.weightOil = ((weightWaxNetto * this.numberOfCandles) * (this.percentageOil / 100)).toFixed(1)
      } else {
        this.weightWax = 0
        this.weightOil = 0
      }
    },
    copyLink () {
      this.showTooltip = true;
      setTimeout(() =>  this.showTooltip = false, 2000);
      navigator.clipboard.writeText('Wax: ' + this.weightWax + 'g, Oil fragrance: ' + this.weightOil + 'g')
    }
  }

}
</script>

