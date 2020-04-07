<template>
  <div style="display: flex;">
    <div v-if="error">{{ error.message }}</div>
    <div v-if="data">
      {{ data }}
    </div>
    <div v-if="!data && !error">Loading...</div>
    <button @click="extra++">more</button> {{extra + count}}
  </div>
</template>

<script lang="ts">
import useSWRV from '../../../../src/use-swrv'
import { ref, watch } from '@vue/composition-api'

const fetcher = (key, timeout = 1000) => {
  return new Promise(res => setTimeout(() => {
    res(key + '_' + Date.now().toString().slice(10, 13))
  }, timeout))
}

export default {
  props: {
    count: {
      type: Number,
      default: 0
    }
  },
  setup (props) {
    const extra = ref(0)
    const { data, error } = useSWRV(() => (extra.value + (props.count as number)).toString(), fetcher, {
      revalidateOnFocus: false
    })

    watch(data, () => {
      // console.log('data changed')
    })

    return {
      data,
      error,
      extra
    }
  }
}
</script>
