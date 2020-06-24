<template>
  <div class="chess-wrapper">
    <div class="chess-header">
      <button class="button-back" @click="goBack()">Вернуться назад</button>
      <div class="chess-header-info">
      <div class="chess-header-info__title">{{ housesChes.objectName }} — {{ housesChes.name }}</div>
      <div class="chess-header-info__description">Адресс: {{housesChes.adress}}</div>
      </div>
    </div>
    <div class="chess-panel">
      <div class="filter">
        <div class="filter-item">
          <div class="fitler-item__title">Кол-во комнат</div>
          <div class="filter-item__filter">
            <el-input-number v-model="filters.rooms" :min="0"></el-input-number>
          </div>
        </div>
        <div class="filter-item">
         <div class="filter-item__title">Стоимость ₽ </div>
          <div class="filter-item__filter">
            <el-input placeholder="От:" v-model="filters.minPrice" class="filter-item__input"></el-input>
            <el-input placeholder="До:" v-model="filters.maxPrice" class="filter-item__input"></el-input>
          </div>
        </div>
        <div class="filter-item">
         <div class="filter-item__title">Площадь м2</div>
          <div class="filter-item__filter">
            <el-input placeholder="От:" v-model="filters.minArea" class="filter-item__input"></el-input>
            <el-input placeholder="До:" v-model="filters.maxArea" class="filter-item__input"></el-input>
          </div>
        </div>
      </div>
      <div class="chess-panel-info" v-if="housesChes && housesChes.apparthaments">
        Всего помещений {{ housesChes.apparthaments.length }} Из них свободных</div>
    <div class="chess-table">
      <div class="chess-table__header">
        <div class="chess-table__porch" v-for="(porch, key) in porches" :key="key">Подъезд {{ porch }}</div>
      </div>
      <div class="chess-table__body">
        <div class="chess-table__item" v-for="(floor, key) in floors" :key="key">
          <div class="chess-table__floor">Этаж {{ floor }}</div>
          <div class="chess-table__sector">
            <div class="chess-table__apparthaments free" v-for="(porch, key) in porches" :key="key">
              <button class="chess-table__apparthament" v-for="(apparthament, key) in getApparthaments(floor, porch)" :key="key" @click="open(apparthament.id)" v-bind:class="{
                free: apparthament.status === 1,
                reserved: apparthament.status === 2,
                sold: apparthament.status === 3,
              }">
                {{ apparthament.countRooms }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    </div>
    <div class="chess-aside" v-if="currentAapparthament">
      <div class="chess-aside__title">Квартира номер <p>{{ currentAapparthament.number}}</p> <button @click="closeAside()">Закрыть мэнэ</button></div>
      <div class="chess-aside__image">
        <img :src="currentAapparthament.img" alt="План Квартиры">
      </div>
      <div class="chess-aside__porch">Подъезд  <p>{{ currentAapparthament.porch}}</p></div>
      <div class="chess-aside__floors">Этаж  <p>{{ currentAapparthament.floors}}</p></div>
      <div class="chess-aside__renovation">Ремонт  <p>{{ currentAapparthament.renovation}}</p></div>
      <div class="chess-aside__room">Количество комнат  <p>{{ currentAapparthament.countRooms}}</p> </div>
      <div class="chess-aside__bathroom">Ванная  <p>{{ currentAapparthament.bathroom}}</p></div>
      <div class="chess-aside__view">Вид из окна  <p>{{ currentAapparthament.windowView}}</p></div>
      <div class="chess-aside__price">Стоимость <p> {{ currentAapparthament.price}} ₽</p></div>
    </div>
    </div>
</template>

<script>
export default {
  name: 'chessView',
  props: {
    housesChes: Object
  },
  data () {
    return {
      filters: {
        rooms: '',
        minPrice: '',
        maxPrice: '',
        minArea: '',
        maxArea: ''
      },
      currentAapparthament: null
    }
  },
  methods: {
    getApparthaments (floor, porch) {
      return this.apparthaments.filter((apparthament) => {
        return apparthament.floor === floor && apparthament.porch === porch
      })
    },
    open (id) {
      this.currentAapparthament = this.housesChes.apparthaments.find((apparthament) => {
        return apparthament.id === id
      })
      console.log(this.currentAapparthament)
    },
    closeAside () {
      this.currentAapparthament = null
    },
    goBack () {
      this.$router.go(-1)
    }
  },
  computed: {
    porches () {
      return Array.from({ length: this.housesChes.countPorches }, (v, i) => i + 1)
    },
    floors () {
      return Array.from({ length: this.housesChes.countFloors }, (v, i) => i + 1).reverse()
    },
    apparthaments () {
      return this.housesChes.apparthaments.filter((apparthament) => {
        if (!!this.filters.rooms && apparthament.countRooms !== this.filters.rooms) {
          return false
        }

        if (!!this.filters.minPrice && apparthament.price < this.filters.minPrice) {
          return false
        }

        return true
      })
    }
  }
}
</script>

<style lang="sass" scoped>
@import '~@/sass/variables.sass'
.button
  &-back
    font-family: 'Roboto'
    font-size: 16px
    border: none
    width: 150px
    height: 30px
    border-radius: 4px
    color: #333333
    background-color: #FFE500
    outline: none
.filter
  display: flex
  justify-content: space-around
  &-item
    &__input
      width: 150px
      &:nth-child(2)
        margin-left: 20px
    &__filter
      margin-top: 15px
.chess
  &-header
    width: 100%
    display: flex
    align-items: center
    box-shadow: 0px 4px 5px 0px rgba(0,0,0,0.1)
    margin-bottom: 15px
    padding: 15px
    &-info
      margin-left: 15px
      &__title
        font-size: 20px
        color: $color-blue
      &__description
        margin-top: 10px
        color: #c4c4c4
  &-table
    width: 100%
    padding: 1rem
    &__floor
      fonts-size: 15px
      color: $color-dark
    &__porch
      color: $color-dark
      font-size: 14px
    &__header
      width: 93%
      margin-left: auto
      display: flex
      justify-content: stretch
    &__item
      display: flex
      padding: 8px 0
    &__sector
      width: 93%
      display: flex
      margin-left: auto
      justify-content: stretch
    &__porch, &__apparthaments
      flex: 1
    &__apparthament
      text-align: center
      font-size: 15px
      width: 20px
      color: #fff
      border: none
      border-radius: 2px
      padding: 3px 6px
      &.free
        background-color: #63cba5
      &.reserved
        background-color: #ffb400
        opacity: 0.5
      &.sold
        background-color: #c4c4c4
        opacity: 0.5
      &:not(:first-child)
        margin-left: 15px
  &-panel
    &-info
      margin-top: 15px
  &-aside
    padding: 0px 8px
    width: 35%
    height: 100vh
    position: absolute
    top: 0
    right: 0
    background-color: #c4c4c4
    &__title, &__image, &__porch, &__floors, &__renovation, &__room, &__bathroom, &__view, &__price
      margin-bottom: 25px
      font-size: 18px
      display: flex
      justify-content: space-betwween
    &__title
      font-size: 24px
    &__image
      width: 100%
      height: 200px
</style>
