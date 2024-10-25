<template>
  <div class="min-h-screen bg-gradient-to-br from-purple-50 to-blue-50">
    <header class="py-6 px-8 border-b bg-white/50 backdrop-blur-sm">
      <div class="max-w-2xl mx-auto">
        <h1
          class="text-3xl font-bold bg-gradient-to-r from-purple-600 to-blue-600 bg-clip-text text-transparent"
        >
          QReate
        </h1>
      </div>
    </header>

    <main class="p-8">
      <div class="max-w-2xl mx-auto">
        <QRCodeGenerator />
      </div>
    </main>

    <footer class="py-6 text-center text-sm text-gray-500">
      Made with ❤️ using Nuxt.js by
      <a href="https://salihg.com/">Salih G.</a>
    </footer>
  </div>
</template>
