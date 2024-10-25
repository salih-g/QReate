<template>
  <div class="bg-gray-50/50 rounded-lg p-4 space-y-4">
    <h3 class="font-medium text-gray-700">Customize Your QR Code</h3>
    <div class="flex flex-col sm:flex-row gap-4">
      <USelect
        :model-value="size"
        @update:model-value="$emit('update:size', $event)"
        :options="[200, 300, 400, 500]"
        label="Size (pixels)"
        class="sm:w-1/2"
      />
      <UColorPicker
        :model-value="color"
        @update:model-value="$emit('update:color', $event)"
        label="QR Code Color"
        class="sm:w-1/2"
      />
    </div>
  </div>
</template>

<script setup>
defineProps({
  size: {
    type: Number,
    required: true,
  },
  color: {
    type: String,
    required: true,
  },
});

defineEmits(['update:size', 'update:color']);
</script>
