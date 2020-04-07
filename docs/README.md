---
home: true
heroText: swrv
heroImage: https://github.com/Kong/swrv/raw/master/logo.png
tagline: swrv documentation
actionText: Get Started →
actionLink: /getting-started/
features:
- title: Feature-rich Data Fetching
  details: Transport and protocol agnostic data fetching, revalidation on focus,
    polling, in-flight de-duplication.
- title: Vue-composition Api
  details: Start developing with power of Vue 3, using the reactivity system of
    the Vue composition api.
- title: Stale-while-revalidate
  details: Uses cache to serve pages fast across all swrv hooks, while 
    revalidating data sources producing an eventually consistent UI.
footer: Copyright © 2020-present Kong
---

`swrv` (pronounced "swerve") is a library using @vue/composition-api hooks for 
remote data fetching. It is largely a port of swr.

The name “SWR” is derived from stale-while-revalidate, a cache invalidation
strategy popularized by HTTP RFC 5861. SWR first returns the data from cache 
(stale), then sends the fetch request (revalidate), and finally comes with the
up-to-date data again.

```vue
<template>
  <div>
    <div v-if="error">failed to load</div>
    <div v-if="!data">loading...</div>
    <div v-else>hello {{ data.name }}</div>
  </div>
</template>

<script>
import useSWRV from 'swrv'

export default {
  name: 'Profile',

  setup() {
    const fetcher = key => fetch(key).then(res => res.json())
    const { data, error } = useSWRV('/api/user', key => fetcher)

    return {
      data,
      error
    }
  }
}
</script>
```

:sparkles: [Read the blogpost](https://guuu.io/2020/data-fetching-vue-composition-api/) 
introducing swrv
