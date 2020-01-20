<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p class="h3">
      <button class="btn btn-primary" @click="vertical">
        {{ (isVertical) ? "Horizontal" : "Vertical" }}
      </button>
      <button class="btn btn-primary ml-3" @click="transition">
        {{ (showTransition) ? "No Transition" : "Transition" }}
      </button>
    </p>

  <Slides :vertical="isVertical" :show-transition="showTransition" />
  
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
      isVertical: false,
      showTransition: true
    }
  },
  methods: {
    vertical () {
      this.isVertical = !this.isVertical
    },
    transition () {
      this.showTransition = !this.showTransition
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
