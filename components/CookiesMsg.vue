<!-- Please remove this file from your project -->
<template>
  <div v-if="cookiesAccept" class="cookies-msg">
    <div class="cookies-msg__box">
      <h3 class="cookies-msg__header">We care about your privacy</h3>
      <p class="cookies-msg__paragraph">We use cookies to personalise content and ads, to provide social media features
        and to analyse our traffic.
        We also share information about your use of our site with our social media, advertising and analytics
        partners.</p>
    </div>
    <div class="cookies-msg__buttons">
      <a class="cookies-msg__button cookies-msg__button--more" target="_blank"
         href="/download/Privacy_Policy_Candle_Calculator.pdf"
      >Find out more</a>
      <button class="cookies-msg__button cookies-msg__button--accept" @click="accept">Yes, I agree</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CandleCalc',
  data () {
    return {
      cookiesAccept: false
    }
  },

  mounted () {
    if (!localStorage.hasOwnProperty('cookies_accept')) {
      this.cookiesAccept = true
    }
  },
  methods: {
    accept () {
      this.cookiesAccept = false
      localStorage.setItem('cookies_accept', Date.now())

    }
  }

}
</script>

