<template>
  <div class="index-header">
    <a
      class="header-item"
      v-for="(item, index) in items" :key="index"
      :href="`#${item.link}`"
    >
      {{ item.name }}
    </a>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'

type HeaderItem = {
  name: string
  link: string
}

@Component
export default class IndexHeader extends Vue {
  @Prop({ default: () => [] })
  items!: HeaderItem[]
}
</script>

<style lang="sass" scoped>
.index-header
  display: flex
  justify-content: space-around
  margin: 0 auto
  padding-top: 16px
  font-family: $sans
  font-weight: 100
  text-transform: uppercase
  font-size: 20px
  width: 360px
</style>
