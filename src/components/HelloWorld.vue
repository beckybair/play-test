<template>
  <div class="hello container">
    <h1>{{ msg }}</h1>
    <p class="h3">
      <button class="btn btn-primary" @click="vertical">
        {{ (isVertical) ? "Horizontal" : "Vertical" }}
      </button>
    </p>

  <Slides :vertical="isVertical" />
  
  </div>
</template>

<script>
import Slides from './Slides'

export default {
  name: 'HelloWorld',
  components: { Slides },
   props: {
    msg: String
  },
  data () {
    return {
      isVertical: false
    }
  },
  methods: {
    vertical () {
      this.isVertical = !this.isVertical
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
