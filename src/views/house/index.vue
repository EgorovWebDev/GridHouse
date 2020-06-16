<template>
  <div class="house">
    <div class="house-wrapper">
      <div class="house-info">
        <div class="house-info__title">{{house.title}}</div>
        <div class="house-info__type">Тип строения: {{house.type}}</div>
        <div class="house-info__stage">Стадия застройки:{{house.stage}}</div>
        <div class="house-info__ready">Этажей готово: {{house.ready}}</div>
        <div class="house-info__floors">Количество этажей: {{house.floors}}</div>
        <div class="house-info__year">Год постройки: {{house.year}}</div>
        <div class="house-info__fz">ФЗ-214: {{house.fz}}</div>
        <button class="button">Шахматка</button>
      </div>
      <div class="house-img">
        <img src="" alt="">
      </div>
    </div>
    <div class="house-buttons">
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
 name: 'houseView'
}
</script>

<style lang="sass" scroped>

</style>