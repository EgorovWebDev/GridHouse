<template>
  <div class="form-container">
    <authorizationView @auth="onAuth($event)"/>
  </div>
</template>

<script>
import authorizationView from '@/views/auth'

export default {
  name: 'authPage',
  components: {
    authorizationView
  },
  methods: {
    onAuth (authData) {
      console.log(authData)
    }
  }
}
</script>

<style lang="sass" scoped>
</style>
