<template>
  <div class="d-flex col-12 mx-0" :class="vertical ? 'col' : 'row'">
    <!-- slider navigation -->
    <div class="navigation" :class="[showNav ? 'd-flex' : 'd-none', vertical ? 'row col-3' : 'align-items-center order-2']">
      <div class="mx-auto" @click="goToPrev"><i :class="`fas fa-chevron-${vertical ? 'up' : 'left'}`"></i></div>
      <div
        v-for="(slide, index) in slides"
        :key="index"
        class="nav-item"
        :class="[index === currentIndex ? 'current' : '']"
        @click="goToSlideIndex(index)"
      >
        <Slide :slide="slide" :navSlide="true" />
      </div>
      <div class="mx-auto" @click="goToNext"><i :class="`fas fa-chevron-${vertical ? 'down' : 'right'}`"></i></div>
    </div>
    <!-- slider -->
    <div class="slides">
      <div
        class="slides-inner"
        :class="{ transition: showTransition }"
        :style="{ width: innerWidth + 'px', marginLeft: '-' + slidesInnerMarginLeft + 'px' }"
      >
        <Slide
          v-for="(slide, i) in slides"
          :key="i"
          :slide="slide"
          :zoomOn="true"
          :style="{ width: singleWidth + 'px' }"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Slide from './Slide'

export default {
  name: 'Slides',
  components: { Slide },
  props: {
    itemsPerSlide: {
      type: null,
      default: 1
    },
    startingIndex: {
      type: null,
      default: 0
    },
    vertical: {
      type: Boolean,
      default: false
    },
    showNav: {
      type: Boolean,
      default: true
    },
    showTransition: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      slides: [
        {src: 'https://source.unsplash.com/collection/993239/600x400'},
        {src: 'https://source.unsplash.com/collection/1673600/600x400'},
        {src: 'https://source.unsplash.com/collection/1513994/600x400'},
        {src: 'https://source.unsplash.com/collection/502925/600x400'},
        {src: 'https://source.unsplash.com/collection/1891993/600x400'}
      ],
      innerWidth: 0,
      singleWidth: 0,
      currentIndex: 0
    }
  },
  computed: {
    slidesInnerMarginLeft () {
      return this.currentIndex * this.singleWidth
    }
  },
  mounted () {
    // console.log(this.$el.lastChild.firstChild.firstChild.firstChild.naturalWidth)
    // this.singleWidth = this.$el.lastChild.firstChild.firstChild.firstChild.naturalWidth
    this.singleWidth = this.$el.clientWidth/this.itemsPerSlide
    this.innerWidth = this.singleWidth * this.slides.length
    this.currentIndex = this.startingIndex
  },
  methods: {
    goToPrev () {
      if (this.currentIndex === 0) {
        this.currentIndex = this.slides.length
      }
      this.currentIndex--
    },
    goToNext () {
      if (this.currentIndex === this.slides.length -1) {
        this.currentIndex = 0 -1
      }
      this.currentIndex++
    },
    goToSlideIndex (index) {
      this.currentIndex = index
    }
  }
}
</script>

<style scoped lang="scss">
.slides {
  overflow: hidden;
  text-align: center;
}
.transition {
  transition: margin 0.6s ease-out;
}
.nav-item {
  margin: 5px;
  background-color: white;
  cursor: pointer;
}
.current {
  border: 3px solid blue;
}
</style>