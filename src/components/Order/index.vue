<template>
  <div class="order-wraper">
    <OrderHeader />
    <OrderBody>
      <OrderBodyForm @submit="handleFormSubmit" @reset="handleFormReset" />
    </OrderBody>
  </div>
</template>

<script lang="ts">
import OrderBody from './OrderBody.vue'
import OrderBodyForm from './OrderBodyForm.vue'
import OrderHeader from './OrderHeader.vue'

export default {
  name: 'OrderVue',
  components: {
    OrderHeader,
    OrderBody,
    OrderBodyForm
  },
  methods: {
    handleFormSubmit(data: any) {
      this.$emit('showPreview', true, data)
    },
    handleFormReset() {
      this.$emit('showPreview', false, {})
    }
  }
}
</script>

<style lang="scss" scoped>
.order-wraper {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
