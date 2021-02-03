<template>
  <base-block>
    <div class="about">

    </div>
  </base-block>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import BaseBlock from '~/components/base/base-block.vue'
@Component({
  components: { BaseBlock }
})
export default class AboutBlock extends Vue {}
</script>

<style lang="sass" scoped>
.about
  height: 100%
  background: $color2
</style>
