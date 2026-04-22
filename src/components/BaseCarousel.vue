<!-- src/components/BaseCarousel.vue -->
<script setup>
import { computed, ref } from 'vue'

const props = defineProps({
  slides: {
    type: Array,
    default: () => [],
  },
  autoplay: {
    type: Boolean,
    default: true,
  },
  interval: {
    type: Number,
    default: 3000,
  },
})

const carouselRef = ref(null)

const handlePrev = () => {
  carouselRef.value?.prev()
}

const handleNext = () => {
  carouselRef.value?.next()
}

const carouselHeight = computed(() => {
  if (typeof window !== 'undefined' && window.innerWidth <= 640) {
    return '220px'
  }
  return '450px'
})
</script>

<template>
  <div class="carousel-shell">
    <div class="carousel-main">
      <el-carousel
        ref="carouselRef"
        :height="carouselHeight"
        :interval="interval"
        :autoplay="autoplay"
        indicator-position="outside"
        arrow="never"
        trigger="click"
      >
        <el-carousel-item v-for="(item, index) in slides" :key="index">
          <div class="slide-inner">
            <img
              :src="item.image"
              :alt="item.alt || `slide-${index}`"
              class="slide-image"
            />
          </div>
        </el-carousel-item>
      </el-carousel>

      <button class="carousel-nav prev" type="button" @click="handlePrev">
        &lt;
      </button>

      <button class="carousel-nav next" type="button" @click="handleNext">
        &gt;
      </button>
    </div>
  </div>
</template>

<style scoped>
.carousel-shell {
  width: 100%;
}

.carousel-main {
  position: relative;
  width: 100%;
}

.slide-inner {
  width: 100%;
  height: 100%;
  overflow: hidden;
  border-radius: 20px;
}

.slide-image {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.carousel-nav {
  position: absolute;
  top: 50%;
  z-index: 10;
  transform: translateY(-50%);
  border: none;
  background: rgba(17, 17, 17, 0.9);
  color: #fff;
  width: 48px;
  height: 48px;
  cursor: pointer;
  transition: 0.2s ease;
}

.carousel-nav:hover {
  opacity: 0.85;
}

.carousel-nav.prev {
  left: 16px;
}

.carousel-nav.next {
  right: 16px;
}

@media (max-width: 640px) {
  .slide-inner {
    border-radius: 14px;
  }

  .carousel-nav {
    width: 38px;
    height: 38px;
    font-size: 14px;
  }

  .carousel-nav.prev {
    left: 8px;
  }

  .carousel-nav.next {
    right: 8px;
  }
}
</style>
