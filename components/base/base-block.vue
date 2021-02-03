<template>
  <div class="base-block">
    <slot />
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'

@Component
export default class BaseBlock extends Vue {}
</script>

<style lang="sass" scoped>
.base-block
  height: 100vh
</style>
