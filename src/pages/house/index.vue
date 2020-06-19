<template>
  <houseView :house="house"/>
</template>

<script>
import houseView from '@/views/house'

import { HOUSES } from '@/store/houses-mock'

export default {
  name: 'housePage',
  components: {
    houseView
  },
  data () {
    return {
      house: {}
    }
  },
  mounted () {
    this.getHouse()
  },
  methods: {
    getHouse () {
      const id = +this.$router.currentRoute.params.id
      this.house = HOUSES.find((house) => house.id === id)
      console.log(this.house)
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
