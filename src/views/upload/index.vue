<template>
  <div class="upload">
    <div v-if="viewedImage" class="upload-container">
      <div
        v-if="viewedImage"
        class="upload-item"
      >
        <div class="upload-hover">
          <i class="el-icon-delete upload-delete" @click="onDelete()"></i>
        </div>
        <img
          :src="viewedImage"
          class="upload-image"
        />
      </div>
    </div>

    <div v-else class="upload-new">
      <input
        type="file"
        accept="image/png, image/jpeg"
        name="image"
        class="upload-input"
        @change="onChange($event)"
      >

      <div class="upload-background">
        <i class="el-icon-plus upload-new__icon"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UploadVue',
  props: ['value'],
  data () {
    return {
      image: ''
    }
  },
  computed: {
    viewedImage () {
      return this.value || this.image
    }
  },
  methods: {
    onChange (event) {
      const file = event.target.files[0]
      const fileUrl = URL.createObjectURL(file)
      this.image = fileUrl
      this.$emit('input', fileUrl)
    },
    onDelete () {
      this.image = ''
      this.$emit('input', '')
    }
  }
}
</script>

<style lang="sass" scoped>
.upload
  &-container
    display: flex
    width: 100%
    flex-wrap: wrap
    margin-bottom: 1.5rem
  &-item
    position: relative
    height: 10rem
    width: 10rem
    margin: 1rem 1rem 0 0
    &:hover .upload-hover
      display: flex
  &-image
    width: 100%
    height: 100%
    object-fit: cover
  &-hover
    display: none
    position: absolute
    width: 100%
    height: 100%
    background-color: rgba(#000000, .3)
    justify-content: center
    align-items: center
  &-delete
    cursor: pointer
    right: -1rem
    top: -1rem
    font-size: 1.5rem
    color: white
  &-new
    position: relative
    height: 10rem
    width: 10rem
    cursor: pointer
    &__icon
      margin: auto
      font-size: 2rem
      color: inherit
    &:hover .form-images-background
      border-color: #555555
  &-background
    border: 1px dashed #999999
    background-color: white
    border-radius: 4px
    width: 100%
    height: 100%
    display: flex
  &-input
    cursor: pointer
    position: absolute
    left: 0
    top: 0
    z-index: 10
    width: 100%
    height: 100%
    opacity: 0
    &:focus ~ .form-images-background
      border-color: #999999
      color: #999999
</style>
