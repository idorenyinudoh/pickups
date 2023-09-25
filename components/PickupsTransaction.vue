<script setup lang="ts">
defineProps({
  numberOfDevices: {
    type: Number,
    required: true
  },
  totalAmount: {
    type: Number,
    required: true
  }
})
</script>

<template>
  <div class="bg-white">
    <div class="px-4 py-2">
      <div class="flex justify-between items-center">
        <p class="text-secondary text-base flex gap-x-1">
          <UIcon class="w-6 h-6 text-[#946E2D]" name="i-heroicons-clock" />
          <span>Payment pending</span>
        </p>
        <UButton class="text-lightpink" icon="i-heroicons-ellipsis-horizontal-20-solid" variant="ghost" />
      </div>
      <div class="py-2 flex justify-between items-end text-secondary text-sm">
        <div>
          <p>Subtotal</p>
          <p class="opacity-50 text-xs">{{ numberOfDevices }} Device<span v-if="numberOfDevices > 1">s</span></p>
        </div>
        <p>${{ totalAmount }}</p>
      </div>
      <div class="py-2 text-secondary text-sm">
        <p>Payment Method</p>
        <p class="text-xs">
          <span class="opacity-50">Cashapp: </span>
          <span class="text-blue">$scga12</span>
        </p>
        <div class="py-1 flex justify-between items-center">
          <p>Total</p>
          <p>${{ totalAmount }}</p>
        </div>
      </div>
    </div>
    <hr class="h-[1px] w-full bg-gray-300" />
    <div class="pt-5 pb-16">
      <UButton class="p-4 px-16 block mx-auto bg-[#0D3455] text-white text-xl font-normal" label="Send Payment" variant="solid" />
    </div>
  </div>
</template>