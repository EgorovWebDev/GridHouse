<template>
  <div class="form form-a">
    <div class="form-title">Авторизация</div>
      <div class="form-info">
      <el-form :model="auth" :rules="rules" >
        <el-form-item label="Почта" prop="mail">
          <el-input v-model.trim="auth.mail" placeholder="Введите почту"></el-input>
        </el-form-item>
        <el-form-item label="Пароль" prop="password">
          <el-input v-model.trim="auth.password" placeholder="Введите пароль"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit(auth)" class="button-empty-b">Войти</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="form-link">
      <div class="form-link__text">Нет аккаунта?</div>
        <router-link :to="{name: 'registration'}">Зарегистрироваться</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'authorizationView',
  data () {
    return {
      auth: {
        mail: '',
        password: ''
      },
      rules: {
        mail: [
          { required: true, message: 'Поле обязательно для заполнения', trigger: ['blur', 'change'] },
          { type: 'email', message: 'email введён неверно', trigger: ['blur', 'change'] }
        ],
        password: [
          { required: true, message: 'Поле обязательно для заполнения', trigger: ['blur', 'change'] },
          { min: 6, message: 'Пароль должен содержарть не менее 5 символов' }
        ]
      }
    }
  },
  methods: {
    onSubmit (auth) {
      console.log(auth)
      if (!this.auth.mail || !this.auth.password) {
        alert('Заполните форму')
      } else {
        this.$router.push('objects')
      }
    }
  }
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
.form
  &-info
    text-align: center
    width: 45%
</style>
