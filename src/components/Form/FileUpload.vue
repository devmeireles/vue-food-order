<template>
  <div class="file-upload">
    <label for="file-upload" class="file-upload__container">
      <div class="file-upload-icon">
        <span>📷</span>
      </div>
      <div class="file-upload__text">
        Jogue aqui o arquivo de imagem do seu pastel ou clique para localizar a pasta.
      </div>
    </label>
    <input @change="handleOnchange" type="file" id="file-upload" accept="image/*" />
  </div>
</template>

<script lang="ts">
export default {
  name: 'FileUpload',
  methods: {
    handleOnchange(event: Event) {
      const input = event.target as HTMLInputElement
      const file = input.files?.[0]

      if (file) {
        const reader = new FileReader()

        reader.onload = (e: ProgressEvent<FileReader>) => {
          this.$emit('imageUpload', e.target?.result as string)
        }

        reader.readAsDataURL(file)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.file-upload {
  input {
    display: none;
  }

  &__container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    cursor: pointer;
    border: 1.5px solid #e43636;
    width: -webkit-fill-available;
    border-radius: 10px;
    padding: 5px 10px;
    color: #a03400;
    height: 110px;
  }
}
</style>
