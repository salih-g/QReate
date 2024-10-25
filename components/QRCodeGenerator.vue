<template>
  <UCard class="backdrop-blur-sm bg-white/80">
    <template #header>
      <div class="space-y-1">
        <h2 class="text-xl font-semibold">Create Your QR Code</h2>
        <p class="text-sm text-gray-500">
          Generate beautiful QR codes in seconds
        </p>
      </div>
    </template>

    <ClientOnly>
      <div class="space-y-8">
        <QRCodeInput v-model="text" @generate="generateQR" />

        <QRCodeOptions v-model:size="size" v-model:color="color" />

        <div class="flex justify-center">
          <UButton
            :loading="generating"
            :disabled="!text"
            @click="generateQR"
            size="lg"
            class="w-full sm:w-auto bg-gradient-to-r from-purple-600 to-blue-600 text-white hover:from-purple-700 hover:to-blue-700 disabled:from-gray-400 disabled:to-gray-400"
            icon="i-heroicons-qr-code"
          >
            Generate QR Code
          </UButton>
        </div>

        <QRCodeDisplay
          v-if="qrCode"
          :qr-code="qrCode"
          :text="text"
          @download="downloadQR"
        />
      </div>
    </ClientOnly>
  </UCard>
</template>

<script setup>
import QRCode from 'qrcode';

const text = ref('');
const size = ref(300);
const color = ref('#000000');
const qrCode = ref('');
const generating = ref(false);

const generateQR = async () => {
  if (!text.value) return;

  generating.value = true;
  try {
    const opts = {
      width: size.value,
      color: {
        dark: color.value,
        light: '#ffffff',
      },
      margin: 1,
    };

    qrCode.value = await QRCode.toDataURL(text.value, opts);
  } catch (err) {
    console.error(err);
  } finally {
    generating.value = false;
  }
};

const downloadQR = () => {
  if (!qrCode.value) return;

  const link = document.createElement('a');
  link.download = 'qreate-qrcode.png';
  link.href = qrCode.value;
  link.click();
};

onMounted(() => {
  watch(
    [text, size, color],
    () => {
      if (text.value) {
        generateQR();
      }
    },
    { debounce: 300 }
  );
});
</script>
