<template>
  <div class="users-wrapper">
    <div class="users">
    <div class="users-info">
      <div class="users-info__login">Логин Пользователя: </div>
      <div class="users-info__password">Пароль Пользователя:</div>
      <div class="users-info__contacts">Контактный номер:</div>
    </div>
    <div class="users-objects">
      <div class="users-objects__contacts">Компания Застройщик:</div>
      <div class="users-objects__contacts">Количество Объектов:</div>
      <div class="users-objects__contacts">Количество Зданий:</div>
    </div>
  </div>
  <div class="users-buttons">
    <button class="button button-yellow" @click="goBack()">назад</button>
    <router-link :to="'/users/edit'" >
      <button class="button button-emptyb button-edit">Редактировать</button>
    </router-link>
  </div>
  </div>
</template>

<script>
export default {
  name: 'usersView',
  methods: {
    goBack () {
      this.$router.go(-1)
    }
  }
}
</script>

<style lang="sass" scoped>
.users
  display: flex
  justify-content: space-between
  &-info, &-objects
    &> div
      margin-bottom: 25px
  &-wrapper
    padding: 15px
  &-buttons
    margin-top: 45px
.button
  &-yellow
    font-family: 'Roboto'
    font-size: 20px
    border: none
    width: 190px
    height: 50px
    border-radius: 4px
    color: #333333
    background-color: #FFE500
    outline: none
    transition: all 0.2s ease
  &-edit
    margin-left: 25px
 </style>
