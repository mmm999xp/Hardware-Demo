<!-- src/views/HomeView.vue -->
<script setup>
import { useRouter } from 'vue-router'
import BaseCarouselElement from '@/components/BaseCarousel.vue'
import ProductCard from '@/components/ProductCard.vue'
import BidCard from '@/components/BidCard.vue'

const router = useRouter()

const banners = [
  {
    image: import.meta.env.BASE_URL + '/cd37d069-65d4-4cf2-9e85-e6c51b67c09e.jpg',
    alt: 'banner 1',
  },
  {
    image: import.meta.env.BASE_URL + '/2420f0bb-e462-4860-8a43-0b547a35789d.jpg',
    alt: 'banner 2',
  },
  {
    image: import.meta.env.BASE_URL + '/acb09497-f081-4f26-8793-b4fa4f17ff86.jpg',
    alt: 'banner 3',
  },
]

const products = [
  {
    name: '商品 1',
    code: 'MB-160',
    image: import.meta.env.BASE_URL + '/andrey-matveev-cQ8wkdZybZc-unsplash.jpg',
    highlight: true,
  },
  {
    name: '商品 2',
    code: 'CF-116C',
    image: import.meta.env.BASE_URL + '/andrey-matveev-vWc2sTyS6sI-unsplash.jpg',
  },
  {
    name: '商品 3',
    code: 'RM-24018',
    image: import.meta.env.BASE_URL + '/andrey-matveev-EKLLxyt-QRE-unsplash.jpg',
  },
  {
    name: '商品 4',
    code: 'TK-084',
    image: import.meta.env.BASE_URL + '/andrey-matveev-iIY-AjQgXsw-unsplash.jpg',
  },
  {
    name: '商品 5',
    code: 'CPU-125',
    image: import.meta.env.BASE_URL + '/andrey-matveev-TZ1iky_p1sc-unsplash.jpg',
  },
  {
    name: '商品 6',
    code: 'HK-220',
    image: import.meta.env.BASE_URL + '/fer-troulik-BILCmJlSHmk-unsplash.jpg',
  },
]

const auctions = [
  {
    title: '拍賣 1',
    endTime: '2026/04/30 21:00',
    startPrice: 8000,
    currentPrice: 12600,
    bidderCount: 12,
    interestedCount: 38,
    image: import.meta.env.BASE_URL + '/fer-troulik-BILCmJlSHmk-unsplash.jpg',
  },
  {
    title: '拍賣 2',
    endTime: '2026/05/01 18:30',
    startPrice: 1500,
    currentPrice: 3200,
    bidderCount: 8,
    interestedCount: 24,
    image: import.meta.env.BASE_URL + '/andrey-matveev-vWc2sTyS6sI-unsplash.jpg',
  },
  {
    title: '拍賣 3',
    endTime: '2026/05/02 20:00',
    startPrice: 1000,
    currentPrice: 2100,
    bidderCount: 5,
    interestedCount: 17,
    image: import.meta.env.BASE_URL + '/andrey-matveev-pfKnGfJrrjI-unsplash.jpg',
  },
  {
    title: '拍賣 4',
    endTime: '2026/05/03 22:00',
    startPrice: 5000,
    currentPrice: 8800,
    bidderCount: 15,
    interestedCount: 41,
    image: import.meta.env.BASE_URL + '/kc-shum-KkaLqA-5XII-unsplash.jpg',
  },
]
const categories = [
  {
    key: 'hand-tools',
    name: '手工具',
    icon: import.meta.env.BASE_URL + '/category' +  '/01.png',
  },
  {
    key: 'power-tools',
    name: '電動工具',
    icon: import.meta.env.BASE_URL + '/category' + '/02.png',
  },
  {
    key: 'measuring-tools',
    name: '測量工具',
    icon: import.meta.env.BASE_URL + '/category' + '/03.png',
  },
  {
    key: 'fasteners',
    name: '螺絲扣件',
    icon: import.meta.env.BASE_URL + '/category' + '/04.png',
  },
  {
    key: 'door-window-hardware',
    name: '門窗五金',
    icon: import.meta.env.BASE_URL + '/category' + '/05.png',
  },
  {
    key: 'plumbing-electrical',
    name: '水電材料',
    icon: import.meta.env.BASE_URL + '/category' + '/06.png',
  },
  {
    key: 'adhesive-sealant',
    name: '黏著密封',
    icon: import.meta.env.BASE_URL + '/category' + '/07.png',
  },
  {
    key: 'paint-repair',
    name: '油漆修繕',
    icon: import.meta.env.BASE_URL + '/category' + '/08.png',
  },
  {
    key: 'safety-protection',
    name: '安全防護',
    icon: import.meta.env.BASE_URL + '/category' + '/09.png',
  },
  {
    key: 'garden-outdoor',
    name: '園藝戶外',
    icon: import.meta.env.BASE_URL + '/category' + '/10.png',
  },
  {
    key: 'storage-transport',
    name: '收納搬運',
    icon: import.meta.env.BASE_URL + '/category' + '/11.png',
  },
  {
    key: 'industrial-consumables',
    name: '工業耗材',
    icon: import.meta.env.BASE_URL + '/category' + '/12.png',
  },
]
</script>

<template>
  <main>
    <div class="carousel-container">
      <BaseCarouselElement
        :slides="banners"
        :autoplay="true"
        :interval="3000"
        class="carousel"
      />
    </div>
    <div class="mx-auto max-w-245 px-4 py-6">

      <div class="mb-4 flex items-center justify-between p-4 lg:px-0">
        <h2 class="text-2xl font-bold">五金分類</h2>
        <a
          class="inline-block rounded bg-zec-green px-3 py-1 text-base font-bold text-black hover:bg-zec-darkgreen"
        >
          更多
        </a>
      </div>
      <section class="grid grid-cols-3 gap-y-8 gap-x-4 py-6 sm:grid-cols-4 lg:grid-cols-6">
        <div
          v-for="category in categories"
          :key="category.key"
          class="flex cursor-pointer flex-col items-center"
        >
          <img
            :src="category.icon"
            :alt="category.name"
            class="h-24 w-24 object-contain sm:h-20 sm:w-20 lg:h-22 lg:w-22"
          >
          <p class="mt-3 text-center text-sm text-zinc-800 sm:text-base">
            {{ category.name }}
          </p>
        </div>
      </section>
    </div>

    <div class="mx-auto max-w-245 px-4 py-6">
      <div class="mb-4 flex items-center justify-between p-4 lg:px-0">
        <h2 class="text-2xl font-bold">猜你喜歡</h2>
        <a
          class="inline-block rounded bg-zec-green px-3 py-1 text-base font-bold text-black hover:bg-zec-darkgreen"
        >
          更多
        </a>
      </div>

      <div class="grid grid-cols-2 gap-4 md:grid-cols-3">
        <ProductCard
          v-for="item in products"
          :key="item.code"
          :product="item"
          class="cursor-pointer"
          @click="router.push('/detail')"
        />
      </div>
    </div>

    <div class="mx-auto max-w-245 px-4 py-6">
      <div class="mb-4 flex items-center justify-between p-4 lg:px-0">
        <h2 class="text-2xl font-bold">熱門競標</h2>
        <a
          class="inline-block rounded bg-zec-green px-3 py-1 text-base font-bold text-black hover:bg-zec-darkgreen"
        >
          更多
        </a>
      </div>

      <div class="grid grid-cols-1 gap-4 md:grid-cols-3">
        <BidCard
          v-for="item in auctions"
          :key="item.title + item.endTime"
          :auction="item"
        />
      </div>
    </div>
  </main>
</template>

<style scoped>
.carousel-container {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 12px;
}

.carousel {
  width: 100%;
  max-width: 980px;
}
</style>
