<template>
  <div v-if="dataReady" class="container">
    <div class="calculator">
      <h1>Candle making calculator</h1>
      <candle-calc @changeValue="changeValue"/>
      <calc-res :weightCandle="weightCandle" :percentageOil="percentageOil" :numberOfCandles="numberOfCandles"/>
    </div>
    <cookies-msg/>
  </div>
</template>

<script>
import CandleCalc from '../components/CandleCalc'
import CalcRes from '../components/CalcRes'
import CookiesMsg from '../components/CookiesMsg'

export default {
  name: 'IndexPage',
  components: {
    CandleCalc,
    CalcRes,
    CookiesMsg
  },
  data () {
    return {
      dataReady: false,
      weightCandle: 0,
      percentageOil: 0,
      numberOfCandles: 0,
    }
  },
  mounted () {
    this.dataReady = true
  },
  methods: {
    changeValue (weightCandle, percentageOil, numberOfCandles) {
      this.weightCandle = parseInt(weightCandle)
      this.percentageOil = parseInt(percentageOil)
      this.numberOfCandles = parseInt(numberOfCandles)
    }
  }
}
</script>
