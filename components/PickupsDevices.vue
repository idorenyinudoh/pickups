<script setup lang="ts">
import Device from '@/utils/types'

const props = defineProps({
  devices: {
    type: Array as PropType<Device[]>,
    required: true
  },
})

const modalIsOpen = ref(false)
const modalImage = ref('')
const toast = useToast()

const handleOpenModal = (index: number) => {
  modalIsOpen.value = true
  modalImage.value = props.devices[index].image
}

const getBase64 = (blob: Blob) => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader()
    reader.readAsDataURL(blob)
    reader.onload = () => resolve(reader.result)
    reader.onerror = (error) => reject(error)
  })
}

const handleImageClick = async (image: string) => {
  const blob = await fetch(`/images/${image}`).then((res) => res.blob())
  const base64 = await getBase64(blob) // here is the base64 string
  toast.add({ title: 'Base64 string generated!', timeout: 7000 })
  modalIsOpen.value = false
}
</script>

<template>
  <div class="relative bg-white">
    <p class="absolute top-0 left-0 px-4 py-2 text-base text-secondary">Devices</p>
    <div v-for="(device, index) in devices" :key="index" :class="['px-4 relative', [ index === 0 ? 'pt-9 pb-5' : 'py-5' ], {'border-b border-solid border-gray-300': index !== devices.length - 1}]">
      <UButton class="absolute top-1 right-4 text-lightpink block ml-auto px-2 py-0 h-5" icon="i-heroicons-ellipsis-horizontal-20-solid" variant="ghost" />
      <div class="flex justify-between items-end">
        <div class="flex gap-x-2 items-center">
          <img :src="`/images/${device.image}`" class="w-10 h-10" alt="">
          <div>
            <p class="text-sm text-secondary">{{ device.name }}</p>
            <p class="text-xs text-secondary/50">{{ device.desc }}</p>
            <p class="text-xs text-blue">Estimated offer ${{ device.offer }}</p>
          </div>
        </div>
        <UButton class="bg-lightpink text-white text-xs" label="Start inspection" @click="handleOpenModal(index)" />
      </div>
    </div>
    <UModal v-model="modalIsOpen">
      <UCard :ui="{ ring: '', divide: 'divide-y divide-gray-100 dark:divide-gray-800' }">
        <template #header>
          <div class="flex items-center justify-between">
            <h3 class="text-base font-semibold leading-6 text-gray-900 dark:text-white">
              Inspect Device
            </h3>
            <UButton color="gray" variant="ghost" icon="i-heroicons-x-mark-20-solid" class="-my-1" @click="modalIsOpen = false" />
          </div>
        </template>
        <div class="py-6">
          <img class="w-3/4 block mx-auto cursor-pointer border-2 border-solid border-transparent rounded-2xl hover:border-lightpink transition-all duration-300" :src="`/images/${modalImage}`" alt="" @click="handleImageClick(modalImage)">
        </div>
      </UCard>
    </UModal>
  </div>
</template>