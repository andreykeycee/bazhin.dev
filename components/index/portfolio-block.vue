<template>
  <base-block>
    <div class="portfolio">

    </div>
  </base-block>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import BaseBlock from '~/components/base/base-block.vue'
@Component({
  components: { BaseBlock }
})
export default class PortfolioBlock extends Vue {}
</script>

<style lang="sass" scoped>
.portfolio
  height: 100%
  background: $color3
</style>
