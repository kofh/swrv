<template>
  <div>
    Hello {{ data }}
  </div>
</template>

<script>
import useSWRV from '../../../../src/use-swrv'

export default {
  setup () {
    return useSWRV('cache-key-2', () => 'SWR')
  }
}
</script>

<style lang="scss" scoped>

</style>
