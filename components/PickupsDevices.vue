<script setup lang="ts">
import Device from '@/utils/types'

defineProps({
  devices: {
    type: Array as PropType<Device[]>,
    required: true
  },
})
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
        <UButton class="bg-lightpink text-white text-xs" label="Start inspection" />
      </div>
    </div>
  </div>
</template>