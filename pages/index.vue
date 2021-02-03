<template>
  <div class="index" ref="index">
    <div class="header">
      <index-header :items="headerItems" />
      <div class="title" :style="{ opacity }">
        {{ title }}
      </div>
    </div>

    <hero-block class="block" id="home"/>
    <about-block class="block" id="about"/>
    <portfolio-block class="block" id="works"/>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import HeroBlock from '~/components/index/hero-block.vue'
import AboutBlock from '~/components/index/about-block.vue'
import PortfolioBlock from '~/components/index/portfolio-block.vue'
import IndexHeader from '~/components/index/index-header.vue'

@Component({
  components: {
    IndexHeader,
    PortfolioBlock,
    HeroBlock,
    AboutBlock
  }
})
export default class IndexPage extends Vue {
  scrollHeight: number = 0
  windowHeight: number = 0
  titles = ['andrey bazhin', 'considers', 'makes']
  opacityRatio = .4
  headerItems = [
    { name: 'home',link: 'home'},
    { name: 'about',link: 'about'},
    { name: 'works',link: 'works'}
  ]

  $refs!: {
    index: HTMLElement
  }

  get title () {
    const currentBlockIndex = Math.floor(
      (this.scrollHeight / this.windowHeight) + this.opacityRatio
    )

    return this.titles[currentBlockIndex]
  }

  get opacity () {
    const positionRatio = this.scrollHeight % this.windowHeight
    const positionRatio2 = (this.windowHeight - positionRatio) / this.windowHeight
    const ratioX10 = this.opacityRatio * 10

    return positionRatio2 < this.opacityRatio
      ? 1 - positionRatio2 * 10 / ratioX10
      : multiplyOnItselfTimes(positionRatio2, ratioX10 / 2)
  }

  mounted () {
    this.windowHeight = window.innerHeight
    this.$refs.index.addEventListener('scroll', this.onScroll)
    window.addEventListener('resize', this.onResize)
  }

  beforeDestroy () {
    window.removeEventListener('resize', this.onResize)
    this.$refs.index.removeEventListener('scroll', this.onScroll)
  }

  onResize () {
    this.onScroll()
    this.windowHeight = window.innerHeight
  }

  onScroll () {
    this.scrollHeight = this.$refs.index.scrollTop
  }
}

const multiplyOnItselfTimes = (num: number, times: number): number => {
  return times
    ? multiplyOnItselfTimes(num * num, times - 1)
    : num
}
</script>

<style lang="sass">
*
  margin: 0

a
  text-decoration: none
  color: inherit

.index
  max-height: 100vh
  overflow-y: scroll
  scroll-snap-type: y mandatory

.block
  scroll-snap-align: start

.header
  width: 100%
  position: absolute
  left: 50%
  transform: translateX(-50%)
  color: $white

.title
  font-family: $fira
  margin-top: 24px
  white-space: nowrap
  font-size: 60px
  text-align: center
</style>
