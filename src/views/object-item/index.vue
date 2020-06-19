<template>
  <div class="object-item">
    <div class="object-item-wrapper">
      <div class="object-item-info">
      <div class="object-item-info__title">{{ object.name }}</div>
      <div class="object-item-info__adress">Адрес: <div>{{ object.address }}</div></div>
      <div class="object-item-info__houses">Домов: <div>{{ object.houses.length }}</div></div>
      <div class="object-item-info__appartaments">Квартир: <div>{{ object.appartaments }}</div></div>
      <div class="object-item-info__buttons">
        <router-link :to="'/objects/' + object.id" >
         <button class="button button-emptyb">Подробней</button>
        </router-link>
        <router-link :to="'/objects/' + object.id + '/edit' " >
          <button class="button button-emptyb button-edit">Редактировать</button>
        </router-link>
      </div>
    </div>
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
              <router-link :to="'/house/' + house.id" >
                <button class="button button-yellow button-slider">Просмотр</button>
              </router-link>
              <router-link :to="'/house/' + house.id" >
                <button class="button button-emptyb button-slider">Шахматка</button>
              </router-link>
            </div>
            </el-carousel-item>
          </el-carousel>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'objectItemView',
  props: {
    object: Object
  }
}
</script>

<style lang="sass" scoped>
.object
  &-item
    width: 90%
    margin: 0 auto
    background-color: #ffffff
    margin-bottom: 30px
    border-radius: 4px
    padding: 35px
    height: 360px
    font-family: 'Roboto'
    box-shadow: -3px 3px 8px 3px rgba(51, 51, 51, 0.29)
    &-info
      max-width: 50%
      &__title
        font-size: 24px
        margin-bottom: 40px
      &__adress, &__houses, &__appartaments
        display: flex
        font-size: 18px
        margin-bottom: 15px
        & > div
          margin-left: 20px
      &> .button-emptyb
        margin-top: 35px
      &__buttons
        margin-top: 87px
    &-wrapper
      display: flex
      justify-content: space-between
.button
  &-edit
    margin-left: 20px
.object
  &-info
    &-carousel
     &__item
      font-size: 20px
      text-align: center
      background-color: #4F4F4F
      border-radius: 5px
      color: #ffffff
    &-slider
      width: 50%
      &__title
       fonts-size: 20px
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
