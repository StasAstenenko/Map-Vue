<script setup>
import { ref } from 'vue'
import UploadIcon from './UploadIcon.vue'

const emit = defineEmits(['uploaded'])
const errorMessage = ref('')

const handleUploadImage = (event) => {
  const file = event.target.files[0]
  const fileReader = new FileReader()

  if (file.size > 3 * 1024 * 1024) {
    return (errorMessage.value = 'Завеликий файл')
  }

  fileReader.readAsDataURL(file)

  fileReader.onload = () => {
    emit('uploaded', fileReader.result)
    errorMessage.value = ''
  }
}
</script>

<template>
  <div>
    <label class="cursor-pointer hover:text-primary">
      <input type="file" accept="image/*" class="hidden" @change="handleUploadImage" />
      <span class="flex gap-1 items-center">
        <UploadIcon />
        <span class="underline text-xs"><slot></slot></span>
      </span>
    </label>
    <div v-if="errorMessage" class="text-red-500">{{ errorMessage }}</div>
  </div>
</template>
