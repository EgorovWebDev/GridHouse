<template>
  <chessView :housesChes="housesChes"/>
</template>

<script>
import chessView from '@/views/chess'

import { HOUSESCHESES } from '@/store/houses-chess-mock'

export default {
  name: 'chessPage',
  components: {
    chessView
  },
  data () {
    return {
      housesChes: {}
    }
  },
  mounted () {
    this.getChess()
  },
  methods: {
    getChess () {
      const id = +this.$router.currentRoute.params.id
      this.housesChes = HOUSESCHESES.find((house) => house.id === id)
    }
  }
}
</script>

<style>

</style>
