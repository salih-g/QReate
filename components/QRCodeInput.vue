<template>
  <UFormGroup label="What would you like to encode?">
    <UTextarea
      :model-value="modelValue"
      @update:model-value="$emit('update:modelValue', $event)"
      :rows="3"
      placeholder="Enter text, URL, contact info, or anything you'd like to turn into a QR code"
      class="w-full"
      color="purple"
    />
  </UFormGroup>
</template>

<script setup>
defineProps({
  modelValue: {
    type: String,
    required: true,
  },
});

defineEmits(['update:modelValue']);
</script>
