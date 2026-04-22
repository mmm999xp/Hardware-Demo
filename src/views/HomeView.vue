<!-- src/views/HomeView.vue -->
<script setup>
import { useRouter } from 'vue-router'
import BaseCarouselElement from '@/components/BaseCarousel.vue'
import ProductCard from '@/components/ProductCard.vue'
import BidCard from '@/components/BidCard.vue'

const router = useRouter()

const banners = [
  {
    image: '/cd37d069-65d4-4cf2-9e85-e6c51b67c09e.jpg',
    alt: 'banner 1',
  },
  {
    image: '/2420f0bb-e462-4860-8a43-0b547a35789d.jpg',
    alt: 'banner 2',
  },
  {
    image: '/acb09497-f081-4f26-8793-b4fa4f17ff86.jpg',
    alt: 'banner 3',
  },
]

const products = [
  {
    name: '商品 1',
    code: 'MB-160',
    image: '/andrey-matveev-cQ8wkdZybZc-unsplash.jpg',
    highlight: true,
  },
  {
    name: '商品 2',
    code: 'CF-116C',
    image: '/andrey-matveev-vWc2sTyS6sI-unsplash.jpg',
  },
  {
    name: '商品 3',
    code: 'RM-24018',
    image: '/andrey-matveev-EKLLxyt-QRE-unsplash.jpg',
  },
  {
    name: '商品 4',
    code: 'TK-084',
    image: '/andrey-matveev-iIY-AjQgXsw-unsplash.jpg',
  },
  {
    name: '商品 5',
    code: 'CPU-125',
    image: '/andrey-matveev-TZ1iky_p1sc-unsplash.jpg',
  },
  {
    name: '商品 6',
    code: 'HK-220',
    image: '/fer-troulik-BILCmJlSHmk-unsplash.jpg',
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
    image: '/fer-troulik-BILCmJlSHmk-unsplash.jpg',
  },
  {
    title: '拍賣 2',
    endTime: '2026/05/01 18:30',
    startPrice: 1500,
    currentPrice: 3200,
    bidderCount: 8,
    interestedCount: 24,
    image: '/andrey-matveev-vWc2sTyS6sI-unsplash.jpg',
  },
  {
    title: '拍賣 3',
    endTime: '2026/05/02 20:00',
    startPrice: 1000,
    currentPrice: 2100,
    bidderCount: 5,
    interestedCount: 17,
    image: '/andrey-matveev-pfKnGfJrrjI-unsplash.jpg',
  },
  {
    title: '拍賣 4',
    endTime: '2026/05/03 22:00',
    startPrice: 5000,
    currentPrice: 8800,
    bidderCount: 15,
    interestedCount: 41,
    image: '/kc-shum-KkaLqA-5XII-unsplash.jpg',
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

    <div class="mx-auto max-w-[980px] px-4 py-6">
      <div class="mb-4 flex items-center justify-between p-4 lg:px-0">
        <h2 class="text-2xl font-bold">猜你喜歡</h2>
        <a
          class="inline-block rounded bg-zec-green px-3 py-1 text-base font-bold text-black hover:bg-zec-darkgreen"
          href="/"
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

    <div class="mx-auto max-w-[980px] px-4 py-6">
      <div class="mb-4 flex items-center justify-between p-4 lg:px-0">
        <h2 class="text-2xl font-bold">熱門競標</h2>
        <a
          class="inline-block rounded bg-zec-green px-3 py-1 text-base font-bold text-black hover:bg-zec-darkgreen"
          href="/"
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
