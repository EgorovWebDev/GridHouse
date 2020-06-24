<template>
  <div class="header-wrapper">
    <header>
      <div class="header-logo">
        <router-link :to="{name: 'objects'}">
          <img src="@/assets/img/icons/logo.svg" alt="GridHouse">
        </router-link>
      </div>
      <ul class='header-nav'>
        <li>
          <router-link :to="{name: 'objects'}">
            Мои Объекты  <i class="el-icon-office-building"></i>
          </router-link>
        </li>
        <li>
          <router-link :to="{name: 'users'}">
          Пользователи <i class="el-icon-user"></i>
          </router-link>
        </li>
        <li>
          <router-link :to="{name: 'settings'}">
            Настройки <i class="el-icon-setting"></i>
          </router-link>
        </li>
      </ul>
      <div class="header-account">
          <router-link :to="{name: 'settings'}">
          <div class="header-account__login">Login</div>
        </router-link>
        <router-link :to="{name: 'auth'}">
          <div class="header-account__exit">
            <img src="@/assets/img/icons/logout.svg" alt="logout">
          </div>
        </router-link>
      </div>
    </header>
    <!-- <div class="mobile-menu">
      <div class="mobile-menu__hamburger" @click="show=!show"></div>
      <ul class="mobile-menu__list">
          <router-link :to="{name: 'objects'}">Мои Объекты</router-link>
          <router-link :to="{name: 'users'}"> Пользователи  </router-link>
          <router-link :to="{name: 'settings'}"> Настройки  </router-link>
          <router-link :to="{name: 'auth'}"> Выход  </router-link>
      </ul>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'headerView'
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
.header-wrapper
  width: 100%
.mobile-menu
  display: none
header
  height: 83px
  background-color: #ffffff
  display: flex
  justify-content: space-around
  align-items: center
  font-family: 'roboto'
  position: fixed
  top: 0
  width: 100vw
  z-index: 100
  box-shadow: 0px 4px 5px 0px rgba(0,0,0,0.34);
ul
  display: flex
  justify-content: space-between
  & > li
    margin: 0 26px
a
  font-family: 'roboto'
  font-size: 18px
  text-decoration: none
  color: #000000
  &:hover
    transition: .5s
    color: #D8C200
i
  margin-left: 6px
  font-size: 24px
.header
  &-account
    display: flex
    &__exit
      img
        width: 24px
        height: 24px
        margin-top: -2px
    &__login
      margin-right: 15px
@media all and (max-width: 992px)
  header
    display: none
  .header
    &-logo
      display: none
  .mobile
    &-menu
      display: block
      width: 100vw
      height: 110vh
      background-color: $color-dark
      position: fixed
      z-index: 1000
      &__hamburger
        width: 50px
        height: 50px
        background-color: #ffffff
        border-radius: 50%
        position: absolute
        top: 25px
        right: 25px
      &__list
        height: 100%
        flex-direction: column
        justify-content: space-around
        text-align: center
        &>a
          font-size: 23px
          letter-spacing: 5px
          color: #ffffff
          text-transform: uppercase
</style>
