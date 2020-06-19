<template>
  <div class="object-wrapper">
  <div class="edit-form">
    <el-form :model="form">
      <el-form-item  label="Название комплекса">
        <el-input v-model="form.name"  placeholder="Название комплекса"></el-input>
      </el-form-item>
    </el-form>
    <el-form ref="form" :model="form">
      <el-form-item label="Широта">
        <el-input v-model="form.latitude" placeholder="Широта"></el-input>
      </el-form-item>
    </el-form>
    <el-form ref="form" :model="form">
      <el-form-item label="Долгота">
        <el-input v-model="form.longitude" placeholder="Долгота"></el-input>
      </el-form-item>
    </el-form>
    <el-form ref="form" :model="form">
      <el-form-item label="Адресс">
        <el-input v-model="form.address" placeholder="Адресс"></el-input>
      </el-form-item>
    </el-form>
    <div class="current-images">
      <div class="current-images__title">Текущие изображения</div>
      <UploadView v-model="form.image"/>
     </div>
  </div>
  {{ form }}
</div>
</template>

<script>
import UploadView from '@/views/upload'

export default {
  name: 'editObjectView',
  data () {
    return {
      form: {
        name: '',
        latitude: '',
        longitude: '',
        address: '',
        image: 'blob:http://localhost:8080/764be5ab-60d7-4e8d-af6f-3b92fd8b56b2'
      }
    }
  },
  components: {
    UploadView
  }
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
.upload-element
  margin-top: 25px
.object-wrapper
  padding: 0px 40px 80px 40px
.current
  &-images
    &__title
      color: $color-dark
      font-family: "Roboto"
</style>
