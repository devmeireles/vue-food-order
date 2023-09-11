<template>
  <div class="form">
    <div class="form-grid">
      <div class="form-grid__field">
        <input
          type="text"
          v-model="formData.title"
          name="title"
          id="order-title"
          placeholder="Título do Pedido"
        />
        <div class="error-message" v-if="v$.formData.title.$error">
          O campo título é obrigatório
        </div>
      </div>
      <div class="form-grid__field">
        <input
          type="text"
          v-model="formData.flavor"
          name="flavor"
          id="order-flavor"
          placeholder="Sabor"
        />
        <div class="error-message" v-if="v$.formData.flavor.$error">
          O campo sabor é obrigatório
        </div>
      </div>
      <div class="form-grid__field">
        <input
          type="text"
          v-model="formData.price"
          name="price"
          id="order-price"
          placeholder="R$"
        />
        <div class="error-message" v-if="v$.formData.price.$error">O campo preço é obrigatório</div>
      </div>
    </div>
    <div class="form-row mt-6">
      <div class="form-row__field">
        <textarea
          v-model="formData.description"
          name="description"
          rows="5"
          id="order-description"
          placeholder="Descrição"
        ></textarea>
      </div>
    </div>
    <div class="form-row mt-6">
      <div class="form-row__field">
        <FileUpload @imageUpload="handleImageUpload" />
      </div>
    </div>

    <div class="form__footer">
      <button type="button" class="btn btn--red" @click="handleReset">Limpar</button>
      <button type="button" class="btn btn--yellow" @click="handleSubmit">Cadastrar</button>
    </div>
  </div>
</template>

<script lang="ts">
import { useVuelidate } from '@vuelidate/core'
import { required } from '@vuelidate/validators'
import FileUpload from '../Form/FileUpload.vue'

export default {
  name: 'OrderBodyForm',
  components: { FileUpload },
  data: () => ({
    formData: {
      title: '',
      flavor: '',
      price: null,
      type: 0,
      description: '',
      image: ''
    },
    v$: useVuelidate()
  }),
  validations: {
    formData: {
      title: { required },
      flavor: { required },
      price: { required }
    }
  },
  computed: {
    isFormInvalid() {
      return true
    }
  },
  methods: {
    handleImageUpload(image: string) {
      if (image) this.formData.image = image
    },

    async handleSubmit() {
      if (await this.v$.$validate()) this.$emit('submit', this.formData)
    },

    handleReset() {
      this.formData = {
        title: '',
        flavor: '',
        price: null,
        type: 0,
        description: '',
        image: ''
      }

      this.$emit('reset', this.formData)
    }
  }
}
</script>

<style lang="scss" scoped>
.form {
  padding: 20px 25px;
  .form-grid {
    display: grid;
    grid-template-columns: repeat(2, 40%) 15%;
    grid-template-rows: 1fr;
    grid-column-gap: 22px;
    grid-row-gap: 0px;
  }

  .error-message {
    color: red;
    font-size: 12px;
    margin-top: 5px;
  }

  &__footer {
    display: flex;
    justify-content: center;
    column-gap: 20px;
    padding-top: 20px;
  }
}
</style>
