<script setup>
defineProps({
  product: {
    type: Object,
    required: true,
  },
})
</script>

<template>
  <div
    class="group aspect-square overflow-hidden  bg-white shadow transition duration-300 hover:-translate-y-1 hover:shadow-xl"
  >
    <div class="flex h-full flex-col">
      <!-- 圖片區 -->
      <div class="flex-1 overflow-hidden bg-white">
        <img
          :src="product.image"
          :alt="product.name"
          class="h-full w-full object-cover object-center transition duration-500 group-hover:scale-105"
        >
      </div>

      <!-- 底部資訊 -->
      <div class="relative overflow-hidden bg-black px-3 py-3 text-center text-white">
        <div
          class="absolute inset-0 bg-gradient-to-r from-red-600 via-red-900 to-black opacity-0 transition duration-300 group-hover:opacity-100"
        />

        <div class="relative z-10 line-clamp-1 text-sm font-semibold md:text-base">
          {{ product.name }}
        </div>

        <div class="relative z-10 mt-1 text-xs text-white/80 md:text-sm">
          {{ product.code }}
        </div>
      </div>
    </div>
  </div>
</template>