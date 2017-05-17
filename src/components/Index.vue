<template>
  <div id="header">
    <common-header></common-header>
    <common-content></common-content>    
  </div>
</template>

<script>
import CommonHeader from './CommonHeader'
import CommonContent from './CommonContent'
export default {
  name: 'hello',
  data () {
    return {
      // msg: 'Welcome to Your Vue.js App'
    }
  },
  components:{ CommonHeader,CommonContent },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
