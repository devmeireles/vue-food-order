<template>
  <div class="order-body w-full">
    <div class="order-body__content">
      <div class="order-body__title">
        <div>
          <p>Monte aqui o seu cardápio. O que está esperando?</p>
        </div>
        <div class="switcher">
          <span class="switcher__label">Comida</span>
          <div class="onoffswitch">
            <input
              type="checkbox"
              name="onoffswitch"
              class="onoffswitch-checkbox"
              id="myonoffswitch"
              tabindex="0"
              checked
            />
            <label class="onoffswitch-label" for="myonoffswitch">
              <span class="onoffswitch-inner"></span>
              <span class="onoffswitch-switch"></span>
            </label>
          </div>
          <span class="switcher__label">Bebida</span>
        </div>
      </div>
      <div class="order-body__form">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'OrderBody'
}
</script>

<style lang="scss" scoped>
.order-body {
  background-color: #fff;
  border-radius: 20px;
  box-shadow: 0px 0px 30px #740b0b45;
  width: 75vw;
  margin-top: -150px;
  overflow: hidden;
  z-index: 10;

  &__content {
    overflow: hidden;
  }

  &__title {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 25px;
    height: 90px;
    background-color: #ffca00;

    p {
      color: #a03400;
      font-size: 24px;
      font-weight: bold;
      font-style: italic;
    }
  }
}
</style>
