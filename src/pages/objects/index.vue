<template>
  <div class="objects">
    <ObjectItemView
      v-for="(object, key) in objects"
      :key="key"
      :object="object"
    />
  </div>
</template>

<script>
import ObjectItemView from '@/views/object-item'

import { OBJECTS } from '@/store/objects-mock'

export default {
  name: 'objectPage',
  components: {
    ObjectItemView
  },
  data () {
    return {
      objects: OBJECTS
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
