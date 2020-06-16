<template>
  <div class="object">
    <div class="object-wrapper">
      <div class="object-info">
        <div class="object-info__title">Жилой комплекс: {{ object.name }}</div>
        <div class="object-info__adress">Адресс: {{ object.address }}</div>
        <div class="object-info__latitude">Широта: {{ object.latitude }}</div>
        <div class="object-info__longitude">Долгота: {{ object.longitude }}</div>
        <div class="object-info__developer">Застройщик: {{ object.developer }}</div>
        <div class="object-info-slider">
          <div class="object-info-slider__title">Дома</div>
         <el-carousel
          :autoplay="false"
          trigger="click"
          type="card"
          indicator-position="outside"
          class="object-info-carousel"
         >
            <el-carousel-item sel-item v-for="(house, key) in object.houses" :key="key" class="object-info-carousel__item">
            <div class="slider-item">
             <div class="slider-item__title">{{ house.name }}</div>
              <div class="slider-item__appartamens">Квартир: {{ house.name.length }}</div>
              <router-link :to="'/houses/' + house.id" >
                <button class="button button-yellow button-slider">Просмотр</button>
              </router-link>
              <router-link :to="'/houses/' + house.id" >
                <button class="button button-emptyb button-slider">Шахматка</button>
              </router-link>
            </div>
            </el-carousel-item>
          </el-carousel>
        </div>
    </div>
    <div class="object-image">
      <img :src="object.image" :alt="'Картинка ' + object.name ">
    </div>
    </div>
      <div class="object-buttons">
        <router-link :to="'/objects'">
          <button class="button button-yellow">Назад</button>
        </router-link>
        <router-link :to="'/objects/' + object.id + '/edit' " >
          <button class="button button-emptyb button-edit">Редактировать</button>
        </router-link>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    object: Object
  },
  name: 'objectView'
}
</script>

<style lang="sass" scoped>
.object
  margin-bottom: 20px
  &-buttons
    margin: 40px 0 30px 40px
  &-wrapper
    display: flex
    justify-content: space-between
    padding: 0 40px
  &-info
    &__title, &__adress, &__latitude, &__longitude, &__developer
      font-size: 18px
      margin-bottom: 40px
    &__title
      font-size: 20px
    &-carousel
      &__item
        width: 250px
        height: 250px
    &-slider
      &__title
        margin-bottom: 25px
  &-image
    max-width: 600px
    height: 630px
  &-carousel
    width: 650px
    height: 450px
    &>img
      width: 100%
      height: 100%
.button
  &-edit
    margin-left: 50px
.object
  &-info
    &-carousel
     &__item
      font-size: 20px
      text-align: center
      background-color: #4F4F4F
      border-radius: 5px
      color: #ffffff
.slider
  &-item
    width: 250px
    height: 250px
    &__title
      margin-top: 25px
    &__appartamens
      margin-top: 20px
.button
  &-slider
    margin-top: 20px
</style>
