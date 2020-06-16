<template>
  <houseView :house="house"/>
</template>

<script>
import houseView from '@/views/house'

import { OBJECTS } from '@/store/objects-mock'

export default {
  name: 'housePage',
  components: {
    houseView
  }
}
</script>

<style lang="sass" scoped>

</style>