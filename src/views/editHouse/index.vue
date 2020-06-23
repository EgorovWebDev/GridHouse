<template>
  <div class="form-wrapper">
    <el-form :model="form" :rules="rules">
        <el-form-item  label="Название дома">
          <el-input v-model="form.name" placeholder="Введите название дома"></el-input>
        </el-form-item>
        <el-form-item label="Тип Застройки">
          <el-select v-model="form.type" placeholder="Выберите тип">
            <el-option label="Панельный" value="shanghai"></el-option>
            <el-option label="Монолитный" value="shanghai"></el-option>
            <el-option label="Кирпичный" value="beijing"></el-option>
            <el-option label="Кирпично-монолитный" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Стадия Застройки">
          <el-select v-model="form.stage" placeholder="Выберите стадию">
            <el-option label="Построен, но не сдан" value="shanghai"></el-option>
            <el-option label="Стан в эксплуатацию" value="shanghai"></el-option>
            <el-option label="Кирпичный" value="beijing"></el-option>
            <el-option label="Кирпично-монолитный" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item  label="Количество готовых этажей">
          <el-input v-model.trim="form.fready"  placeholder="Введите количество готовых этажей"></el-input>
        </el-form-item>
        <el-form-item  label="Количество этажей">
          <el-input v-model.trim="form.fcount"  placeholder="Введите количество этажей"></el-input>
        </el-form-item>
        <el-form-item  label="Год постройки">
          <el-input v-model.trim="form.year"  placeholder="Введите год постройки"></el-input>
        </el-form-item>
          <el-form-item label="ФЗ-214">
             <el-switch v-model="form.fz"></el-switch>
          </el-form-item>
    </el-form>
    <div class="current-images">
      <div class="current-images__title">Текущие изображения</div>
      <UploadView v-model="form.image"/>
     </div>
    {{ form }}
  </div>
</template>

<script>
import UploadView from '@/views/upload'

export default {
  name: 'editHouseView',
  components: {
    UploadView
  },
  data () {
    return {
      form: {
        name: '',
        type: '',
        stage: '',
        fready: '',
        fcount: '',
        year: '',
        fz: false,
        image: ''
      },
      rules: {
        name: [
          { required: true, message: 'Please input Activity name', trigger: 'blur' }
        ]
      }
    }
  }
}
</script>

<style lang="sass" scoped>
  .form
    &-wrapper
      padding: 0px 40px 80px 40px
</style>
