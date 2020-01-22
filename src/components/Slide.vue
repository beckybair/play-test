<template>
  <div
    class="slide"
    :class="navSlide ? 'd-inline-block' : 'd-inline-flex justify-content-center'"
  >
    <zoom-on-hover
      v-if="!navSlide && zoomOn"
      :img-normal="slide.src"
      img-alt="testing alt"
      img-class="img-fluid"
      scale="2"
    />
    <img v-else class="img-fluid" :src="slide.src" alt="">
    <!-- Use slot here so could use html instead of just image -->
  </div>
</template>

<script>
import ZoomOnHover from './ZoomOnHover'
export default {
  name: 'Slide',
  components: { ZoomOnHover },
  props: {
    slide: {
      type: Object,
      default: () => {}
    },
    navSlide: {
      type: Boolean,
      default: false
    },
    zoomOn: {
      type: Boolean,
      default: false
    }
  }
}
</script>
