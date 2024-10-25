<template>
  <div class="flex flex-col items-center gap-6 py-4">
    <div class="bg-white rounded-xl shadow-lg p-6 w-fit">
      <img :src="qrCode" :alt="text" class="max-w-full h-auto" />
    </div>
    <UButton
      @click="$emit('download')"
      size="lg"
      class="bg-gradient-to-r from-purple-600 to-blue-600 text-white hover:from-purple-700 hover:to-blue-700"
      icon="i-heroicons-arrow-down-tray"
    >
      Download QR Code
    </UButton>
  </div>
</template>

<script setup>
defineProps({
  qrCode: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
});

defineEmits(['download']);
</script>
