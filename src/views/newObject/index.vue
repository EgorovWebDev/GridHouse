<template>
  <div class="object-wrapper">
  <div class="new-form">
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
      <div class="current-images__title">Добавить картинку изображения</div>
     </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'newObjectView',
  data () {
    return {
      form: {
        name: '',
        latitude: '',
        longitude: '',
        address: ''
      }
    }
  }
}
</script>

<style lang="sass" scoped>
.object
  &-wrapper
    padding: 0px 40px 40px 40px
</style>