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
  <main class="relative w-2/4 min-w-[300px] max-w-[400px] max-h-[80vh] overflow-y-scroll mx-auto my-[10vh] border border-solid border-gray-300 bg-gray-100 flex flex-col gap-y-4">
    <PickupsIntro />
    <PickupsDevices :devices="devices" />
    <PickupsTransaction
      :number-of-devices="devices.length"
      :total-amount="devices.reduce((acc, cur) => acc + cur.offer, 0)"
    />
    <nav class="sticky bottom-0 left-0 w-full p-2 flex justify-between items-center bg-white shadow-[0_1px_5px_gray]">
      <UButton class="block" variant="ghost">
        <UIcon class="w-6 h-6 text-blue" name="i-heroicons-chat-bubble-left-ellipsis-solid" />
        <p class="text-secondary leading-3" style="font-size: 10px;">Chats</p>
      </UButton>
      <UButton class="block" variant="ghost">
        <UIcon class="w-6 h-6 text-blue" name="i-heroicons-calendar-days-solid" />
        <p class="text-secondary leading-3" style="font-size: 10px;">Schedule</p>
      </UButton>
      <UButton class="block" variant="ghost">
        <UIcon class="w-6 h-6 text-blue" name="i-heroicons-map-pin" />
        <p class="text-blue leading-3" style="font-size: 10px;">Pickups</p>
      </UButton>
      <UButton class="block" variant="ghost">
        <UIcon class="w-6 h-6 text-blue" name="i-heroicons-credit-card-solid" />
        <p class="text-secondary leading-3" style="font-size: 10px;">Earnings</p>
      </UButton>
      <UButton class="block" variant="ghost">
        <UIcon class="w-6 h-6 text-blue" name="i-heroicons-user" />
        <p class="text-secondary leading-3" style="font-size: 10px;">Account</p>
      </UButton>
    </nav>
  </main>
</template>
