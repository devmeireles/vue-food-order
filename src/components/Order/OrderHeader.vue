<template>
  <div class="order-header">
    <div class="order-header__title">
      <img src="@/assets/images/logo.png" class="order-header__image" alt="Pastel das Ideias" />
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'OrderHeader'
}
</script>

<style lang="scss" scoped>
.order-header {
  width: 100%;
  &__title {
    background-image: url('@/assets/images/wave.png');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: top left;
    height: 375px;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    width: 100%;
  }

  &__image {
    max-height: 200px;
    padding-top: 2rem;
  }
}
</style>
