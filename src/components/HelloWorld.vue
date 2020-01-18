<template>
  <div class="hello container">
    <h1>{{ msg }}</h1>

  <Slides />
  
  </div>
</template>

<script>
import Slides from './Slides'

export default {
  name: 'HelloWorld',
  components: { Slides },
   props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
