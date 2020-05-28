<template>
  <div class="objects">
    <ObjectItemView
      v-for="(object, key) in objects"
      :key="key"
      :object="object"
    />
    <div class="objects-new">
      <router-link :to="'/objects/new'" ><i class="el-icon-plus"></i></router-link>
    </div>
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
.objects
  &-new
    width: 60px
    height: 60px
    background-color: #ffffff
    position: fixed
    bottom: 50px
    right: 80px
    border-radius: 50%
    transition: all 0.4s ease
    &:hover
      transform: scale(1.2)
      transition: all 0.4s ease
  i
    color: #333333
    font-size: 45px
    margin-top: 9px
    margin-left: 8px
</style>
