<template>
  <div class="wrapper">
    <div class="preview">
      <div class="preview__header">
        <div class="preview__title">
          {{ title }}
        </div>

        <div class="preview__price">R${{ price }}</div>
      </div>

      <div class="preview__body">
        <div v-if="image" class="preview__image">
          <img :src="image" :alt="title" />
        </div>

        <div class="preview__content">
          <span><strong>Sabor: </strong> {{ flavor }}</span>
          <span><strong>Descrição: </strong> {{ description }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'OrderPreview',
  props: {
    title: {
      type: String,
      default: ''
    },
    price: {
      type: Number,
      default: 0
    },
    flavor: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  justify-content: center;
  padding-top: 50px;
}

.preview {
  width: 75vw;
  box-shadow: 0px 0px 30px #740b0b45;
  overflow: hidden;
  border-radius: 20px;
  background-color: #fff;
  z-index: 10;

  &__header {
    background: #e43636;
    height: 80px;
    display: flex;
    justify-content: space-between;
    padding: 20px 30px;
    font-size: 30px;
    font-style: italic;
  }

  &__title {
    color: #ffca00;
  }

  &__price {
    color: #fff;
  }

  &__body {
    display: flex;
    min-height: 220px;
  }

  &__image {
    background: #fff;
    width: 250px;
    display: flex;
    justify-content: center;
  }

  &__content {
    display: flex;
    flex-direction: column;
    padding: 20px;
    color: #a03400;
    font-size: 24px;
  }
}
</style>
