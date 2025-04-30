<script setup>
import { computed, reactive, toRaw } from 'vue'
import IButton from '../IButton/IButton.vue'
import MarkerIcon from '../icons/MarkerIcon.vue'
import IInput from '../IInput/IInput.vue'
import IModal from '../IModal/IModal.vue'
import InputImage from '../InputImage/InputImage.vue'

const props = defineProps({
  isOpen: {
    default: false,
    type: Boolean,
  },
})

const emit = defineEmits(['close', 'submit'])
const formData = reactive({
  title: '',
  description: '',
  img: '',
})

const handleUploadImage = (url) => {
  formData.img = url
}

const uploadText = computed(() => {
  return formData.img ? 'Натисніть тут, щоб змінити фото' : 'Натисніть тут, щоб додати фото'
})
</script>

<template>
  <IModal v-if="props.isOpen" @close="emit('close')">
    <form @submit.prevent="emit('submit', toRaw(formData))">
      <div class="min-w-[420px]">
        <div class="flex gap-1 justify-center mb-10 fon-bold text-center">
          <MarkerIcon /> Додати маркери
        </div>
        <IInput label="Локація" class="mb-4" v-model="formData.title" />
        <IInput label="Опис" type="textarea" class="mb-2" v-model="formData.description" />
        <div class="flex gap-1 items-center mb-10">
          <img v-if="formData.img" :src="formData.img" alt="avatar" class="object-cover w-8 h-8" />
          <InputImage @uploaded="handleUploadImage">{{ uploadText }}</InputImage>
        </div>

        <IButton class="w-full">Додати</IButton>
      </div>
    </form>
  </IModal>
</template>
