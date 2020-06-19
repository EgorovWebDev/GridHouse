<template>
  <div class="house">
    <div class="house-wrapper">
      <div class="house-info">
        <div class="house-info__title">Название: {{ house.name }}</div>
        <div class="house-info__type">Тип строения: {{ house.type }}</div>
        <div class="house-info__stage">Стадия застройки:{{ house.stage }}</div>
        <div class="house-info__ready">Этажей готово: {{ house.ready }}</div>
        <div class="house-info__floors">Количество этажей: {{ house.floors }}</div>
        <div class="house-info__year">Год постройки: {{ house.year }}</div>
        <div class="house-info__fz">ФЗ-214: {{ house.fz }}</div>
        <router-link :to="'/chess/id'">
        <button class="button button-yellow">Шахматка</button>
      </router-link>
      </div>
      <div class="house-image">
        <img :src="house.image" :alt="'Картинка ' + house.name ">
      </div>
    </div>
    <div class="house-buttons">
      <router-link :to="'/house'">
        <button class="button button-yellow">Назад</button>
      </router-link>
      <router-link :to="'/house/' + house.id_object + '/edit' " >
        <button class="button button-emptyb button-edit">Редактировать</button>
      </router-link>
    </div>
  </div>
</template>

<script>

export default {
  name: 'houseView',
  props: {
    house: Object
  }
}
</script>

<style lang="sass" scroped>
  .house
    margin-bottom: 20px
    &-wrapper
      display: flex
      justify-content: space-between
      padding: 0 40px
    &-buttons
      margin: 40px 0 30px 40px
    &-image
      min-width: 450px
      max-width: 600px
      height: 630px
    &-info
      max-width: 50%
      &__type, &__ready, &__floors, &__year, &__fz, &__stage, &__title
        overflow-wrap: break-word
        word-break: break-all
        font-size: 20px
        margin-bottom: 35px
      &__title
        margin-bottom: 35px
        font-size: 25px
  .button
    &-edit
      margin-left: 50px

</style>
