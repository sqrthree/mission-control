<template>
  <div class="copyright">
    <p>Copyright {{ year }} {{ version }}</p>
    <p v-if="debug">Build at {{ buildAt }}</p>
  </div>
</template>

<script>
export default {
  name: 'TheCopyright',
  computed: {
    year() {
      const date = new Date()

      return date.getFullYear()
    },
    version() {
      return `v${BUILD_INFO.version}`
    },
    buildAt() {
      return new Date(BUILD_INFO.time).toLocaleString()
    },
    debug() {
      return this.$store.state.config.debug
    },
  },
}
</script>

<style lang="scss">
@import '~@/styles/app';

.copyright {
  font-size: 12px;
  text-align: center;
  user-select: none;

  @include theme-light {
    color: theme-light('dispensable-info-text-color');
  }

  @include theme-dark {
    color: theme-dark('dispensable-info-text-color');
  }
}
</style>
