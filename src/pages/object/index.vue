<template>
  <objectView :object="object"/>
</template>

<script>
import objectView from '@/views/object'

import { OBJECTS } from '@/store/objects-mock'

export default {
  name: 'objectPage',
  components: {
    objectView
  },
  data () {
    return {
      object: {}
    }
  },
  mounted () {
    this.getObject()
  },
  methods: {
    getObject () {
      const id = +this.$router.currentRoute.params.id
      this.object = OBJECTS.find((object) => object.id === id)
    }
  }
}
</script>

<style lang="sass" scoped></style>
