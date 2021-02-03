<template>
  <base-block>
    <div class="hero">

    </div>
  </base-block>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import BaseBlock from '~/components/base/base-block.vue'
@Component({
  components: { BaseBlock }
})
export default class HeroBlock extends Vue {}
</script>

<style lang="sass" scoped>
.hero
  background: $color1
  height: 100%
</style>
