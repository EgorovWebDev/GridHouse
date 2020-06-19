<template>
  <div class="settings">
    <settingsView
      v-for="(object, key) in objects"
      :key="key"
      :object="object"
    />
  </div>
</template>

<script>
import settingsView from '@/views/settings'

import { OBJECTS } from '@/store/objects-mock'

export default {
  name: 'settingsPage',
  components: {
    settingsView
  },
  data () {
    return {
      objects: OBJECTS
    }
  }
}
</script>

<style lang="sass" scoped>
@media all and (max-width: 850px)
  .settings
    display: flex
    flex-wrap: wrap
</style>
