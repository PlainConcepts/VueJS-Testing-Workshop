<template lang="html">
<section class="cities container-medium">
  <header class="cities-header text-big">{{'cities.title' | t }}</header>
  <router-view></router-view>
</section>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class CitiesComponent extends Vue {}
</script>
<style lang="scss">
@import '~styles/variables';

.cities {
  &-header {
    color: $color-primary;
  }
}
</style>
