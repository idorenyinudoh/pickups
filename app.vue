<script setup lang="ts">
import Device from '@/utils/types'

const devices = reactive<Device[]>([
  {
    image: 'iphone13-pro-max.jpeg',
    name: 'iPhone 13 Pro Max',
    desc: '128GB - Unlocked - Flawless',
    offer: 750
  },
  {
    image: 'iphone13.webp',
    name: 'iPhone 13',
    desc: '128GB - Unlocked - Good',
    offer: 550
  }
])
</script>

<template>
  <main class="w-2/4 min-w-[300px] max-w-[400px] max-h-[80vh] overflow-y-scroll mx-auto my-[10vh] border border-solid border-gray-300 bg-gray-100 flex flex-col gap-y-4">
    <PickupsIntro />
    <PickupsDevices :devices="devices" />
    <PickupsTransaction
      :number-of-devices="devices.length"
      :total-amount="devices.reduce((acc, cur) => acc + cur.offer, 0)"
    />
  </main>
</template>
