<template>
  <div class="slide d-inline-flex justify-content-center">
    <img class="img-fluid" :src="slide.src" alt="">
    <!-- Use slot here so could use html instead of just image -->
  </div>
</template>

<script>
export default {
  name: 'Slide',
  props: {
    slide: {
      type: Object,
      default: () => {}
    }
  },
  data () {
    return {

    }
  }
}
</script>
