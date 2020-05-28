<template>
  <div class="form form-a">
    <div class="form-title">Авторизация</div>
      <div class="form-info">
      <el-form ref="formAuth" :model="auth" :rules="rules">
        <el-form-item label="Почта" prop="mail">
          <el-input v-model="auth.mail" placeholder="Введите почту"></el-input>
        </el-form-item>
        <el-form-item label="Пароль" prop="password">
          <el-input v-model="auth.password" placeholder="Введите почту"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit" class="button-empty-b">Войти</el-button>
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
          { required: true, message: 'Поле обязательно для заполнение', trigger: 'blur' },
          { type: 'email', message: 'email введён не корректно', trigger: ['blur', 'change'] }
        ],
        password: [
          { required: true, message: 'Поле обязательно для заполнение', trigger: 'blur' },
          { type: 'password', message: 'Поле обязательно для заполнение', trigger: ['blur', 'change'] }
        ]
      }
    }
  },
  methods: {
    onSubmit () {
      this.$emit('auth', this.auth)
    }
  }
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
</style>
