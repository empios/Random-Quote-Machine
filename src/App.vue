<template>
  <div id="app" class="hero is-fullheight">
    <div class="hero-body">
      <QuoteBox/>
    </div>
  </div>
</template>

<script>
import QuoteBox from './components/QuoteBox.vue'

export default {
  name: 'App',
  components: {
    QuoteBox
  }
}
</script>

<style>
  #app{
    width:100%;
    height: 100%;
    background-color: aquamarine;
  }
</style>
