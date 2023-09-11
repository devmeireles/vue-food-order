<template>
  <div class="parallax">
    <img class="floating-image" src="@/assets/images/pastel-parallax.png" alt="Floating Image" />
  </div>

  <main class="home-view">
    <Order @showPreview="handleShowPreview" />
    <OrderPreview
      v-if="showPreview"
      :title="previewData.title"
      :price="previewData.price"
      :flavor="previewData.flavor"
      :description="previewData.description"
      :image="previewData.image"
    />
  </main>
</template>

<script lang="ts">
import Order from '@/components/Order/index.vue'
import OrderPreview from '@/components/OrderPreview/index.vue'
import { type IOrder } from '@/types/Order'

export default {
  name: 'HomeView',
  components: {
    Order,
    OrderPreview
  },
  data: () => ({
    previewData: {} as IOrder,
    showPreview: false
  }),
  methods: {
    handleShowPreview(show: boolean, data: IOrder) {
      this.showPreview = show
      this.previewData = data
    }
  }
}
</script>

<style lang="scss" scoped>
.home-view {
  min-height: 100vh;
  padding-bottom: 200px;
  background-image: url('@/assets/images/pattern.png');
}

.parallax {
  position: fixed;
  overflow: hidden;
  z-index: 1;
  height: 300px;
  width: 300px;

  .floating-image {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 300px;
    animation: floatAnimation 5s ease-in-out infinite alternate;
  }
}

@keyframes floatAnimation {
  0% {
    transform: translateX(-50%) translateY(0);
  }
  100% {
    transform: translateX(-50%) translateY(-20px);
  }
}
</style>
