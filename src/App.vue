<script setup>
import { RouterView } from 'vue-router'
import { useRouter } from 'vue-router'
const router = useRouter()
</script>

<template>
  <div>
    <nav class="site-header">
      <div class="nav-inner">
        <div class="brand cursor-pointer" @click="router.push('/')">
          <img src="/logo.png" alt="logo" class="brand-logo" />
        </div>

        <div class="btns">
          <button class="btn btn-line">Line 登入</button>
          <button class="btn btn-text">登入</button>
          <button class="btn btn-primary">註冊</button>
        </div>
      </div>
    </nav>

    <RouterView />
  </div>
</template>

<style scoped>
.site-header {
  position: sticky;
  top: 0;
  z-index: 20;
  background: rgba(223, 226, 230, 0.75);
  backdrop-filter: blur(8px);
}

.nav-inner {
  min-height: 68px;
  padding: 12px 14px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  background: #ffffff;
  border: 1px solid #e8edf2;
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.08);
}

.brand {
  flex: 0 0 auto;
  display: flex;
  align-items: center;
}

.brand-logo {
  height: 34px;
  width: auto;
  display: block;
  object-fit: contain;
}

.btns {
  flex: 1;
  min-width: 0;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 10px;
  flex-wrap: nowrap;
}

.btn {
  min-width: 100px;
  height: 40px;
  padding: 0 14px;
  border: 1px solid transparent;
  border-radius: 999px;
  font-size: 15px;
  font-weight: 700;
  white-space: nowrap;
  cursor: pointer;
  transition:
    transform 0.2s ease,
    background-color 0.2s ease,
    border-color 0.2s ease,
    color 0.2s ease,
    box-shadow 0.2s ease;
}

.btn:hover {
  transform: translateY(-1px);
}

.btn-line {
  background: #06c755;
  color: #ffffff;
  box-shadow: 0 8px 18px rgba(6, 199, 85, 0.22);
}

.btn-line:hover {
  background: #05b54d;
}

.btn-text {
  background: #f8fafc;
  border-color: #dbe3eb;
  color: #334155;
}

.btn-text:hover {
  background: #eef2f6;
}

.btn-primary {
  background: #1f2937;
  color: #ffffff;
}

.btn-primary:hover {
  background: #111827;
}

@media (max-width: 640px) {
 

  .nav-inner {
    min-height: 60px;
    padding: 10px;
    gap: 8px;
  }

  .brand-logo {
    height: 26px;
  }

  .btns {
    gap: 8px;
  }

  .btn {
    height: 36px;
    padding: 0 8px;
    font-size: 13px;
  }
}

@media (max-width: 420px) {
  .nav-inner {
    gap: 6px;
  }

  .brand-logo {
    height: 22px;
  }

  .btns {
    gap: 6px;
  }

  .btn {
    height: 34px;
    padding: 0 6px;
    font-size: 12px;
    letter-spacing: 0;
  }
}
</style>

