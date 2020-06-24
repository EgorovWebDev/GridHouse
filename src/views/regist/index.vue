<template>
  <div class="form form-r">
    <div class="form-title">Регистрация</div>
    <div class="form-info">
      <el-form ref="form-reg" :model="reg" :rules="rules">
        <el-form-item label="Почта" prop="mail">
          <el-input v-model="reg.mail" placeholder="Введите почту" required></el-input>
        </el-form-item>
        <el-form-item label="Пароль" prop="password">
          <el-input v-model="reg.password" placeholder="Введите пароль"></el-input>
        </el-form-item>
        <el-form-item label="Повторите пароль" prop="reqPassword">
          <el-input v-model="reg.reqPassword" placeholder="Повторите пароль"></el-input>
        </el-form-item>
        <div class="form-agreement" prop="agree">
          <el-checkbox name="type" v-model="reg.agree">
          </el-checkbox>
            <div class="form-agreement__text">Я даю согласие на <router-link :to="{name: 'agreement'}">обработку персональных даннных</router-link></div>
        </div>
        <div class="form-button__wrapper">
          <el-form-item>
            <el-button type="primary" @click="onSubmit(reg)" class="button-empty-b" >Зарегистрироваться</el-button>
          </el-form-item>
        </div>
      </el-form>
    </div>
    <div class="form-link">
      <div class="form-link__text">Уже есть аккаунт?</div>
        <router-link :to="{name: 'auth'}">Войти</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'registrarionView',
  data () {
    return {
      reg: {
        mail: '',
        password: '',
        passwordConfirm: '',
        agree: false
      },
      rules: {
        mail: [
          { required: true, message: 'Поле обязательно для заполнения', trigger: ['blur', 'change'] },
          { type: 'email', message: 'email введён неверно', trigger: ['blur', 'change'] }
        ],
        password: [
          { required: true, message: 'Поле обязательно для заполнения', trigger: ['blur', 'change'] },
          { min: 6, message: 'Пароль должен содержарть не менее 5 символов' }
        ],
        reqPassword: [
          { required: true, message: 'Поле обязательно для заполнения', trigger: ['blur', 'change'] },
          { min: 6, message: 'Пароль должен содержарть не менее 5 символов' }
        ],
        agree: [
          { required: true, message: 'Please input activity form', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    onSubmit (reg) {
      console.log(reg)
      if (!this.reg.mail || !this.reg.password || !this.reg.reqPassword || this.reg.agree === false) {
        alert('Заполните форму')
      } else {
        this.$router.push('auth')
      }
    }
  }
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
.form
  &-agreement
    display: flex
    &__text
      margin-left: 15px
      width: 80%
      &> a
        text-decoration: none
        color: $color-blue
  &-button
    &__wrapper
      text-align: center
      width: 100%
@media all and (max-width: 500px)
  .form
    &-agreement
      align-items: center
      &__text
        width: unset
        font-size: 16px
@media all and (max-width: 450px)
  .form
    &-agreement
      &__text
        font-size: 14px
</style>
