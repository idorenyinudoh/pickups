<script setup lang="ts">
const offerId = ref('T216')
const offerPaymentStatus = ref('Pending payment')
const offerStatus = ref('Assigned')
const pickupDate = ref('March 6')
const pickupTime = ref('11am - 12pm')
const earnings = ref('$30')
const customerName = ref('Christopher Nunez')
const customerPhone = ref('+1 (516) 812-9200')
const pickupAddress = ref('3001 Fulton St, Brooklyn, NY 11208')
const pickupAddressDistance = ref('1.5 mi away from my location')
const pickupAddressInstructions = ref('Please call 10 min before arrival.')
</script>

<template>
  <div class="bg-white">
    <TheLocation />
    <div class="my-2 mx-5 flex gap-x-2 justify-center items-center text-xs">
      <p class="text-primary px-2 py-1 rounded-2xl border border-solid border-primary">Offer {{ offerId }}</p>
      <p class="text-secondary bg-[#F9D896] px-2 py-1 rounded-2xl">{{ offerPaymentStatus }}</p>
      <p class="text-secondary bg-grey px-2 py-1 rounded-2xl">{{ offerStatus }}</p>
    </div>
    <div class="my-4 flex gap-x-10 justify-center items-center">
      <div class="flex gap-x-2 items-center">
        <UIcon class="w-10 h-10 text-primary" name="i-heroicons-calendar-days-solid" color="primary" />
        <div>
          <p class="text-secondary/50 text-sm">Date</p>
          <p class="text-secondary text-sm">{{ pickupDate }}</p>
        </div>
      </div>
      <div class="flex gap-x-2 items-center">
        <UIcon class="w-10 h-10 text-primary" name="i-heroicons-clock" />
        <div>
          <p class="text-secondary/50 text-sm">Time</p>
          <p class="text-secondary text-sm">{{ pickupTime }}</p>
        </div>
      </div>
    </div>
    <div
      class="mx-8 my-2 px-7 py-3 rounded-xl border border-solid border-blue bg-blue-100 flex justify-between items-center">
      <p class="text-sm text-secondary">You will earn</p>
      <p class="text-xl text-blue">{{ earnings }}</p>
    </div>
    <hr class="h-[1px] w-full bg-gray-300" />
    <div class="py-2 px-4 flex justify-between items-center">
      <div class="text-sm text-secondary max-w-[50%]">
        <p class="opacity-50">Customer</p>
        <p>{{ customerName }}</p>
        <p class="text-xs">{{ customerPhone }}</p>
      </div>
      <div class="flex gap-x-3 items-center">
        <UButton class="!bg-grey block px-3 py-1">
          <UIcon class="w-7 h-7 text-blue" name="i-heroicons-chat-bubble-oval-left-solid" />
          <p class="text-blue leading-3" style="font-size: 10px;">Msg</p>
        </UButton>
        <UButton class="!bg-grey block px-3 py-1">
          <UIcon class="w-7 h-7 text-blue" name="i-heroicons-phone-solid" />
          <p class="text-blue leading-3" style="font-size: 10px;">Call</p>
        </UButton>
      </div>
    </div>
    <hr class="h-[1px] w-full bg-gray-300" />
    <div class="py-2 px-4 flex justify-between items-center">
      <div class="text-sm text-secondary max-w-[50%]">
        <p class="opacity-50">Pickup address</p>
        <p>{{ pickupAddress }}</p>
        <p class="text-xs text-blue flex gap-x-1 items-center">
          <UIcon class="w-3 h-3" name="i-heroicons-map-pin" />
          <span>{{ pickupAddressDistance }}</span>
        </p>
      </div>
      <div class="flex gap-x-3 items-center">
        <UButton class="!bg-[#78E677] !text-white p-4 text-xl font-normal" label="GO">
        </UButton>
      </div>
    </div>
    <hr class="h-[1px] w-full bg-gray-300" />
    <div class="py-2 px-4">
      <div class="text-sm text-secondary">
        <p class="opacity-50">Address instructions</p>
        <p>{{ pickupAddressInstructions }}</p>
      </div>
    </div>
  </div>
</template>