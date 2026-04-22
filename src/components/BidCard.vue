<script setup>
defineProps({
  auction: {
    type: Object,
    required: true,
  },
})

const formatPrice = value => {
  return new Intl.NumberFormat('zh-TW').format(value)
}
</script>

<template>
  <div
    class="group  overflow-hidden  border border-black/10 bg-white shadow-sm transition duration-300 hover:-translate-y-1 hover:shadow-xl"
  >
    <div class="flex h-full flex-col">
      <!-- 圖片區 -->
      <div class="relative flex-1 overflow-hidden bg-neutral-100">
        <img
          :src="auction.image"
          :alt="auction.title"
          class="h-full w-full object-cover object-center transition duration-500 group-hover:scale-105"
        >

        <!-- 狀態標籤 -->
        <div
          class="absolute left-3 top-3 inline-flex items-center rounded-full bg-black/80 px-3 py-1 text-xs font-semibold text-white backdrop-blur-sm"
        >
          競標中
        </div>
      </div>

      <!-- 底部資訊 -->
      <div class="bg-white px-4 py-4 text-black transition duration-300 group-hover:bg-neutral-50">
        <div>
          <!-- 標題 -->
          <div class="line-clamp-1 text-base font-bold md:text-lg">
            {{ auction.title }}
          </div>

          <!-- 截標時間 -->
          <div class="mt-2 flex items-center gap-2 text-sm text-black/60">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.8"
              class="h-4 w-4 shrink-0"
            >
              <circle cx="12" cy="12" r="9" />
              <path d="M12 7v5l3 2" />
            </svg>
            <span class="truncate">{{ auction.endTime }}</span>
          </div>

          <!-- 價格區 -->
          <div class="mt-3 grid grid-cols-2 gap-2">
            <div class=" px-3 py-2 transition duration-300">
              <div class="text-[11px] text-black/45">起標金額</div>
              <div class="mt-1 text-sm font-semibold text-black">
                NT$ {{ formatPrice(auction.startPrice) }}
              </div>
            </div>

            <div class=" px-3 py-2 transition duration-300 ">
              <div class="text-[11px] text-black/45">目前最高價</div>
              <div class="mt-1 text-sm font-bold text-red-600">
                NT$ {{ formatPrice(auction.currentPrice) }}
              </div>
            </div>
          </div>

          <!-- 底部統計 -->
          <div class="mt-3 flex flex-wrap gap-2">
            <!-- 競標人數 -->
            <div
              class="inline-flex items-center gap-1.5  px-3 py-1.5 text-xs text-black/75 transition duration-300 "
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="1.8"
                class="h-4 w-4"
              >
                <path d="M14 19a6 6 0 0 0-12 0" />
                <circle cx="8" cy="9" r="4" />
                <path d="M22 19a6 6 0 0 0-4-5.65" />
                <path d="M16 4.35a4 4 0 0 1 0 7.3" />
              </svg>
              <span>{{ auction.bidderCount }} 人競標</span>
            </div>

            <!-- 人氣 -->
            <div
              class="inline-flex items-center gap-1.5  px-3 py-1.5 text-xs text-orange-600 transition duration-300 "
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="currentColor"
                class="h-4 w-4"
              >
                <path
                  d="M12.59 2.07c.2-.29.62-.02.46.28-.72 1.36-.3 2.52.18 3.83.35.97.74 2.05.74 3.36 0 1.44-.67 2.64-1.67 3.47.12-1.25-.16-2.16-.85-3.06-.17-.21-.5-.12-.54.14-.18 1.08-.8 1.91-1.46 2.8-.95 1.28-1.99 2.69-1.99 4.92 0 3.08 2.42 5.25 5.54 5.25 3.36 0 5.5-2.45 5.5-5.48 0-3.02-1.67-4.9-3.11-6.53-1.14-1.28-2.13-2.39-2.8-4.19Z"
                />
              </svg>
              <span>{{ auction.interestedCount }} 人有興趣</span>
            </div>
          </div>

          <!-- 按鈕 -->
          <button
            type="button"
            class="mt-4 w-full  border border-black bg-black px-4 py-2.5 text-sm font-semibold text-white transition hover:bg-gradient-to-r hover:from-red-600 hover:via-red-900 hover:to-black"
          >
            馬上出價
          </button>
        </div>
      </div>
    </div>
  </div>
</template>