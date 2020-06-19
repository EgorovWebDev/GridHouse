<template>
  <div class="settings-card">
    <div class="settings-card__title">{{ object.name }}</div>
    <div class="settings-card__houses">Домов:{{ object.houses.length }}</div>
    <div class="settings-card__appartaments">Квартир:{{ object.appartaments }}</div>
    <button class="button button-emptyb settings-card__export" @click="doExport">Экспорт</button>
    <button class="button button-emptyb settings-card__delete" @click="doDelete">Удалить</button>
  </div>
</template>

<script>
export default {
  name: 'settingsView',
  props: {
    object: Object
  },
  methods: {
    doExport () {
      alert('Объект ' + this.object.name + ' экспортирован')
    },
    doDelete () {
      alert('Объект ' + this.object.name + ' удалён')
    }
  }
}
</script>

<style lang="sass" scoped >
.settings
  &-card
    border-radius: 5px
    align-items: center
    display: flex
    justify-content: space-between
    padding: 15px
    margin: 15px
    height: 100px
    box-shadow: -3px 3px 8px 3px rgba(51, 51, 51, 0.29)
    &__export, &__delete
      width: 120px
      height: 40px
    &__delete
      border: 2px solid #EB1515
      color: #EB1515
@media all and (max-width: 850px)
  .settings
    &-card
      width: 45%
      height: 250px
      flex-direction: column
@media all and (max-width: 610px)
  .settings
    &-card
      text-align: center
      width: 100%
      height: 350px
      &__title
        font-size: 24px
        margin-top: 15px
      &__houses, &__appartaments
        font-size: 20px
      &__export, &__delete
        width: 190px
        heigth: 50px
</style>
