<script setup>
import { computed, ref } from 'vue'

const encodeSvg = svg => `data:image/svg+xml;charset=UTF-8,${encodeURIComponent(svg)}`

const createPhotoSvg = ({
  title,
  subtitle,
  accent = '#f97316',
  secondary = '#111827',
  background = '#f3f4f6',
}) =>
  encodeSvg(`
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 900">
      <defs>
        <linearGradient id="bg" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="${background}" />
          <stop offset="100%" stop-color="#d6dae0" />
        </linearGradient>
        <linearGradient id="metal" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#f8fafc" />
          <stop offset="100%" stop-color="#94a3b8" />
        </linearGradient>
      </defs>
      <rect width="1200" height="900" fill="url(#bg)" />
      <circle cx="1030" cy="170" r="130" fill="${accent}" opacity="0.18" />
      <circle cx="220" cy="750" r="180" fill="${secondary}" opacity="0.1" />
      <rect x="100" y="110" width="1000" height="680" rx="44" fill="#ffffff" />
      <rect x="144" y="150" width="912" height="600" rx="32" fill="#161616" />
      <rect x="240" y="205" width="500" height="18" rx="9" fill="${accent}" opacity="0.95" />
      <text x="240" y="292" fill="#ffffff" font-size="72" font-family="Arial, Helvetica, sans-serif" font-weight="800">${title}</text>
      <text x="240" y="348" fill="#d1d5db" font-size="30" font-family="Arial, Helvetica, sans-serif">${subtitle}</text>
      <g transform="translate(760 170) rotate(-18)">
        <rect x="0" y="0" width="70" height="350" rx="28" fill="${accent}" />
        <rect x="46" y="26" width="360" height="22" rx="11" fill="url(#metal)" />
        <rect x="392" y="6" width="66" height="62" rx="14" fill="#cbd5e1" />
        <rect x="412" y="18" width="24" height="38" rx="8" fill="${secondary}" />
      </g>
      <g transform="translate(722 372) rotate(20)">
        <rect x="0" y="0" width="240" height="34" rx="16" fill="#cbd5e1" />
        <circle cx="212" cy="17" r="42" fill="#e5e7eb" stroke="#94a3b8" stroke-width="16" />
      </g>
      <g transform="translate(770 498) rotate(14)">
        <rect x="0" y="0" width="250" height="36" rx="18" fill="#e2e8f0" />
        <path d="M250 18 L334 18" stroke="#94a3b8" stroke-width="18" stroke-linecap="round" />
        <path d="M333 18 l40 -24 v48 z" fill="${accent}" />
      </g>
      <g transform="translate(668 610) rotate(-10)">
        <rect x="0" y="0" width="170" height="40" rx="18" fill="#334155" />
        <rect x="128" y="-36" width="40" height="112" rx="14" fill="#f8fafc" />
      </g>
      <g transform="translate(300 546)">
        <rect x="0" y="0" width="256" height="120" rx="26" fill="#f8fafc" opacity="0.11" stroke="#ffffff" stroke-opacity="0.2" />
        <text x="36" y="48" fill="#ffffff" font-size="24" font-family="Arial, Helvetica, sans-serif">72 齒棘輪 / 18 合 1 批頭</text>
        <text x="36" y="86" fill="#fdba74" font-size="34" font-family="Arial, Helvetica, sans-serif" font-weight="700">DIY / 居家 / 車用 / 維修</text>
      </g>
    </svg>
  `)

const createSceneSvg = ({ title, accent, icon, mood }) =>
  encodeSvg(`
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 560">
      <defs>
        <linearGradient id="sceneBg" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#101828" />
          <stop offset="100%" stop-color="#293241" />
        </linearGradient>
      </defs>
      <rect width="800" height="560" fill="url(#sceneBg)" />
      <rect x="48" y="48" width="704" height="464" rx="36" fill="#ffffff" opacity="0.08" />
      <circle cx="640" cy="132" r="96" fill="${accent}" opacity="0.25" />
      <text x="72" y="118" fill="#ffffff" font-size="54" font-family="Arial, Helvetica, sans-serif" font-weight="700">${icon}</text>
      <text x="72" y="190" fill="#ffffff" font-size="46" font-family="Arial, Helvetica, sans-serif" font-weight="800">${title}</text>
      <text x="72" y="244" fill="#d1d5db" font-size="26" font-family="Arial, Helvetica, sans-serif">${mood}</text>
      <g transform="translate(94 318)">
        <rect x="0" y="0" width="290" height="28" rx="14" fill="#e5e7eb" opacity="0.85" />
        <rect x="0" y="44" width="240" height="28" rx="14" fill="${accent}" opacity="0.82" />
        <rect x="0" y="88" width="320" height="28" rx="14" fill="#94a3b8" opacity="0.7" />
      </g>
      <g transform="translate(510 282) rotate(-12)">
        <rect x="0" y="0" width="48" height="180" rx="16" fill="${accent}" />
        <rect x="36" y="20" width="170" height="18" rx="9" fill="#e5e7eb" />
        <rect x="194" y="6" width="44" height="46" rx="12" fill="#cbd5e1" />
      </g>
    </svg>
  `)

const createPackSvg = ({ title, accent }) =>
  encodeSvg(`
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 460">
      <rect width="600" height="460" rx="44" fill="#161616" />
      <rect x="42" y="42" width="516" height="376" rx="30" fill="#ffffff" opacity="0.07" />
      <rect x="94" y="106" width="148" height="220" rx="24" fill="${accent}" />
      <rect x="194" y="136" width="222" height="32" rx="16" fill="#e5e7eb" />
      <rect x="194" y="194" width="160" height="32" rx="16" fill="#cbd5e1" />
      <rect x="194" y="252" width="198" height="32" rx="16" fill="#e5e7eb" opacity="0.86" />
      <text x="92" y="386" fill="#ffffff" font-size="34" font-family="Arial, Helvetica, sans-serif" font-weight="800">${title}</text>
    </svg>
  `)

const createMotionSvg = ({ accent, title, type }) => {
  const scenes = {
    ratchet: `
      <g transform="translate(74 150)">
        <rect x="0" y="0" width="130" height="44" rx="20" fill="${accent}">
          <animateTransform attributeName="transform" type="rotate" values="-8 65 22;8 65 22;-8 65 22" dur="2.4s" repeatCount="indefinite" />
        </rect>
        <rect x="102" y="12" width="210" height="20" rx="10" fill="#dbeafe">
          <animateTransform attributeName="transform" type="rotate" values="-8 65 22;8 65 22;-8 65 22" dur="2.4s" repeatCount="indefinite" />
        </rect>
        <rect x="294" y="2" width="54" height="40" rx="12" fill="#f8fafc">
          <animateTransform attributeName="transform" type="rotate" values="-8 65 22;8 65 22;-8 65 22" dur="2.4s" repeatCount="indefinite" />
        </rect>
      </g>
      <circle cx="334" cy="172" r="62" fill="${accent}" opacity="0.18">
        <animate attributeName="r" values="50;64;50" dur="2.4s" repeatCount="indefinite" />
      </circle>
    `,
    magnetic: `
      <g transform="translate(88 134)">
        <rect x="0" y="78" width="250" height="24" rx="12" fill="#e5e7eb" />
        <rect x="66" y="0" width="58" height="88" rx="20" fill="${accent}">
          <animate attributeName="y" values="0;26;0" dur="1.8s" repeatCount="indefinite" />
        </rect>
        <circle cx="94" cy="122" r="18" fill="#fff7ed">
          <animate attributeName="cy" values="122;94;122" dur="1.8s" repeatCount="indefinite" />
        </circle>
        <circle cx="146" cy="122" r="18" fill="#fff7ed">
          <animate attributeName="cy" values="122;82;122" dur="1.8s" repeatCount="indefinite" />
        </circle>
        <circle cx="198" cy="122" r="18" fill="#fff7ed">
          <animate attributeName="cy" values="122;100;122" dur="1.8s" repeatCount="indefinite" />
        </circle>
      </g>
    `,
    storage: `
      <g transform="translate(56 126)">
        <rect x="0" y="0" width="316" height="162" rx="28" fill="#111827" />
        <rect x="22" y="24" width="272" height="112" rx="20" fill="#1f2937" />
        <g>
          <rect x="42" y="44" width="28" height="72" rx="10" fill="${accent}">
            <animate attributeName="x" values="42;210;42" dur="2.6s" repeatCount="indefinite" />
          </rect>
          <rect x="88" y="44" width="28" height="72" rx="10" fill="#f8fafc" opacity="0.8" />
          <rect x="134" y="44" width="28" height="72" rx="10" fill="#cbd5e1" opacity="0.9" />
          <rect x="180" y="44" width="28" height="72" rx="10" fill="#94a3b8" opacity="0.9" />
          <rect x="226" y="44" width="28" height="72" rx="10" fill="#e5e7eb" opacity="0.9" />
        </g>
      </g>
    `,
  }

  return `
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 420 320" class="motion-svg">
      <rect width="420" height="320" rx="30" fill="#0f172a" />
      <rect x="20" y="20" width="380" height="280" rx="24" fill="#ffffff" opacity="0.06" />
      <text x="34" y="56" fill="#ffffff" font-size="28" font-family="Arial, Helvetica, sans-serif" font-weight="800">${title}</text>
      ${scenes[type]}
    </svg>
  `
}

const campaign = ref({
  brand: 'ForgeMax',
  title: 'ForgeMax M24 模組化棘輪手工具組',
  subtitle: '一盒收齊常用棘輪、批頭、套筒與延長桿，從居家維修到工作桌拆裝都更俐落。',
  description:
    '不是把工具做得更多，而是把每一次出手都做得更準。ForgeMax M24 以「高頻使用場景」重新整理工具邏輯，把最常用的扭、拆、鎖、換，濃縮進一套可隨手提走的手工具組，讓你在家修櫃體、鎖家具、拆機殼、調腳踏車時，都能用更少的動作，完成更漂亮的收尾。',
  fundingPercent: 268,
  fundedAmount: 2684200,
  goal: 1000000,
  supporters: 4126,
  daysLeft: 19,
  earlyBirdPrice: 2680,
  originalPrice: 3980,
})

const storyBlocks = [
  {
    kicker: '為什麼做這套',
    title: '工具不是越多越好，而是越順手越好',
    content:
      '你一定也有過這種經驗。明明只是想鎖一顆螺絲，卻得在工具箱裡翻半天；找到規格後，角度又卡、手又酸，還得一直換握姿。ForgeMax M24 想解決的，就是這些看似小事、卻每天都在消耗效率的時刻。',
  },
  {
    kicker: '我們的做法',
    title: '用一套真正會被拿出來用的工具，取代一堆躺在角落的配件',
    content:
      '從棘輪齒數、握把比例、磁吸批頭固定、收納順序到盒體打開的視覺辨識，我們都以「快速找到、快速上手、快速收回」為核心設計。它不是陳列型工具，而是一套每天都願意拿出來工作的工具。',
  },
]

const highlights = [
  {
    icon: '01',
    title: '72 齒細緻棘輪',
    desc: '5 度回擺即可咬合，狹小角度也能順利施力，櫃體背板、機車側蓋、桌下結構都更好操作。',
  },
  {
    icon: '02',
    title: '磁吸快拆批頭',
    desc: '換頭流暢、定位清楚，常用十字、一字、Torx、六角都能迅速切換，不拖泥帶水。',
  },
  {
    icon: '03',
    title: '一盒帶走高頻規格',
    desc: '從家具組裝、家電外殼、腳踏車調整到電腦升級，常見需求一盒內就能直接應對。',
  },
]

const featureSections = [
  {
    id: 'ratchet',
    kicker: '核心亮點',
    title: '小角度也能連續出力，棘輪手感乾脆俐落',
    body:
      'ForgeMax M24 採用 72 齒棘輪結構，回擺角度更小，意味著你在桌腳內側、牆邊轉角、機械殼體這種不好施力的位置，不必一直拔起重轉。每一下都能接續發力，速度更快，手腕負擔也更低。',
    bullets: [
      '高密度齒輪咬合，鎖付手感紮實不虛位',
      '正反向切換撥桿明確，戴手套也能快速辨識',
      '握把比例加大，長時間使用不容易手心發麻',
    ],
    image: createPhotoSvg({
      title: '72 TOOTH RATCHET',
      subtitle: '為高頻拆裝而生的順手節奏',
      accent: '#f97316',
      secondary: '#0f172a',
      background: '#ece7df',
    }),
  },
  {
    id: 'bits',
    kicker: '批頭系統',
    title: '批頭與套筒配置，專為日常高使用率整理',
    body:
      '常用規格不是越多越有感，而是拿起來第一時間就能找到。M24 把最常用的十字、一字、六角、梅花與套筒依照實際任務排序，避免你每次都從一整排陌生配件裡重新辨識。',
    bullets: [
      '批頭表面防滑噴砂，減少打滑與崩牙機率',
      '延長桿與萬向接頭組合，死角位置照樣可進',
      '套筒尺寸覆蓋居家與輕維修常用需求',
    ],
    image: createPhotoSvg({
      title: '18-IN-1 BIT SYSTEM',
      subtitle: '把常用規格排在最順手的位置',
      accent: '#16a34a',
      secondary: '#111827',
      background: '#e7eef4',
    }),
  },
]

const motionDemos = [
  {
    title: '棘輪回擺示意',
    desc: '不必整支離開螺絲頭重新定位，來回擺動就能持續出力，狹窄位置尤其有感。',
    motionSvg: createMotionSvg({
      accent: '#f97316',
      title: 'Ratchet Motion',
      type: 'ratchet',
    }),
  },
  {
    title: '磁吸快拆示意',
    desc: '批頭吸附與拆換更俐落，常用規格切換快，不用一直低頭找零件。',
    motionSvg: createMotionSvg({
      accent: '#22c55e',
      title: 'Magnetic Bit Swap',
      type: 'magnetic',
    }),
  },
  {
    title: '收納排序示意',
    desc: '打開工具盒就能直覺找到下一個規格，收工後也能快速回位，避免散亂。',
    motionSvg: createMotionSvg({
      accent: '#38bdf8',
      title: 'Organized Storage',
      type: 'storage',
    }),
  },
]

const useScenarios = [
  {
    title: '家具組裝',
    desc: '櫃體、書桌、層架、椅腳安裝更省時，鎖付節奏更連貫。',
    image: createSceneSvg({
      title: '家具組裝',
      accent: '#f97316',
      icon: 'DIY',
      mood: '房間裡就能完成漂亮組裝',
    }),
  },
  {
    title: '電腦升級',
    desc: '機殼側板、風扇、顯卡固定與周邊小螺絲拆裝都更精準。',
    image: createSceneSvg({
      title: '電腦升級',
      accent: '#0ea5e9',
      icon: 'PC',
      mood: '拆機不再手忙腳亂',
    }),
  },
  {
    title: '腳踏車與車庫',
    desc: '坐墊、配件、燈具、支架與車內小部件維護，一盒就能應付。',
    image: createSceneSvg({
      title: '車庫維護',
      accent: '#22c55e',
      icon: 'GARAGE',
      mood: '從日常保養到臨時調整都好用',
    }),
  },
  {
    title: '工作桌整理',
    desc: '螢幕支架、鍵盤托架、抽屜滑軌與辦公小物快速調整。',
    image: createSceneSvg({
      title: '工作桌整理',
      accent: '#a855f7',
      icon: 'DESK',
      mood: '桌面更俐落，維護更有效率',
    }),
  },
]

const comparisonRows = [
  {
    label: '棘輪結構',
    pro: '72 齒細緻回擺，窄角度也能連續作業',
    normal: '回擺角度較大，狹窄位置常需重抓角度',
  },
  {
    label: '常用規格收納',
    pro: '依使用頻率排序，打開即可直覺取用',
    normal: '規格零散，使用前先找一輪',
  },
  {
    label: '握把手感',
    pro: '止滑包覆與掌心撐托兼顧，久用較不疲勞',
    normal: '偏硬或偏細，長時間施力容易酸手',
  },
  {
    label: '攜帶效率',
    pro: '一盒整套帶走，移動與收工都快',
    normal: '工具分散，臨時工作容易漏帶規格',
  },
]

const boxItems = [
  { name: '72 齒棘輪主柄', qty: 'x1', image: createPackSvg({ title: '72T RATCHET', accent: '#f97316' }) },
  { name: '批頭延長桿', qty: 'x1', image: createPackSvg({ title: 'EXTENSION', accent: '#0ea5e9' }) },
  { name: '萬向接頭', qty: 'x1', image: createPackSvg({ title: 'UNIVERSAL', accent: '#22c55e' }) },
  { name: '常用套筒組', qty: 'x8', image: createPackSvg({ title: 'SOCKETS', accent: '#eab308' }) },
  { name: '十字 / 一字 / Torx 批頭', qty: 'x12', image: createPackSvg({ title: 'BITS', accent: '#8b5cf6' }) },
  { name: '硬殼工具盒', qty: 'x1', image: createPackSvg({ title: 'CASE', accent: '#334155' }) },
]

const materials = [
  {
    title: 'CR-V 鋼材本體',
    desc: '兼顧硬度與韌性，面對高頻扭力輸出更耐用，長期使用依然維持穩定手感。',
  },
  {
    title: '霧面止滑握把',
    desc: '掌心貼合不黏手，潮濕環境也能維持足夠摩擦力，施力更有信心。',
  },
  {
    title: '耐磨表面處理',
    desc: '降低日常刮傷與氧化痕跡，讓工具在常用狀態下依舊保持乾淨俐落。',
  },
  {
    title: '分區硬殼收納',
    desc: '每一格都有固定位置，攜帶時不易混亂，拿取與收回都更有秩序。',
  },
]

const specs = [
  { label: '產品名稱', value: 'ForgeMax M24 模組化棘輪手工具組' },
  { label: '內容件數', value: '24 件常用配置' },
  { label: '棘輪規格', value: '72 齒 / 正反切換 / 快拆結構' },
  { label: '主要材質', value: 'CR-V 鋼、TPR 止滑握把、PP 硬殼盒' },
  { label: '工具盒尺寸', value: '285 x 198 x 63 mm' },
  { label: '總重量', value: '約 1.85 kg' },
]

const testimonials = [
  {
    name: '阿哲',
    role: '租屋族 / 家具組裝重度使用',
    text: '以前買平價工具最怕的就是不好施力，鎖到一半還得重新抓角度。這套最有感的是棘輪手感很乾脆，桌腳和層架那種卡手位置也能順順做完。',
  },
  {
    name: 'Mina',
    role: '內容創作者 / 工作桌設備控',
    text: '我常常在換螢幕支架、整理拍攝設備，最討厭找不到對的批頭。ForgeMax M24 打開就能直接辨識，收工也不會散一桌，對我這種常移動設備的人非常友善。',
  },
  {
    name: 'Kevin',
    role: '腳踏車通勤族',
    text: '不用再準備一大袋工具出門，平常調整坐墊、燈架、配件固定，用這一盒就很夠。延長桿加萬向接頭那段真的很實用，很多角度都救得到。',
  },
]

const faqs = ref([
  {
    q: '這套適合完全沒有工具基礎的人嗎？',
    a: '很適合。M24 的配置就是以日常高頻任務為核心，規格不會多到讓人無從下手，收納位置也清楚，第一次使用也能快速理解。',
    open: true,
  },
  {
    q: '它比較偏居家用途，還是偏專業工作使用？',
    a: '它最擅長的是居家維修、辦公設備整理、腳踏車與輕型車庫保養、3C 與家具組裝等高頻場景。若是高強度專業工地需求，仍建議搭配專門規格工具。',
    open: false,
  },
  {
    q: '批頭和套筒會不會很容易散掉？',
    a: '不會。每個配件都有固定槽位，盒體關起後也有穩定扣合設計，攜帶時不容易鬆脫或整盒亂位。',
    open: false,
  },
  {
    q: '這頁面的動態示意是真的 GIF 嗎？',
    a: '這版頁面使用 SVG 動畫模擬 GIF 效果，載入更輕，視覺上仍能清楚展示工具切換與使用節奏。',
    open: false,
  },
])

const progressWidth = computed(() => `${Math.min(campaign.value.fundingPercent, 100)}%`)
const savings = computed(() => campaign.value.originalPrice - campaign.value.earlyBirdPrice)

const formatPrice = value => new Intl.NumberFormat('zh-TW').format(value)

const toggleFaq = index => {
  faqs.value[index].open = !faqs.value[index].open
}
</script>

<template>
  <div class="detail-page bg-[#f4f1ea] text-[#111827]">
    <section class="hero-section overflow-hidden bg-[#121212] text-white">
      <div class="hero-glow hero-glow-left" />
      <div class="hero-glow hero-glow-right" />

      <div class="mx-auto grid max-w-7xl gap-10 px-4 py-10 lg:grid-cols-[1.1fr_0.9fr] lg:px-8 lg:py-16">
        <div class="relative z-10 flex flex-col justify-center">
          <div class="inline-flex w-fit items-center rounded-full bg-white/10 px-4 py-2 text-sm font-semibold tracking-[0.2em] text-orange-300">
            HAND TOOLS CAMPAIGN
          </div>

          <p class="mt-6 text-sm font-bold uppercase tracking-[0.35em] text-orange-400">
            {{ campaign.brand }}
          </p>

          <h1 class="mt-4 text-4xl font-black leading-tight md:text-6xl">
            {{ campaign.title }}
          </h1>

          <p class="mt-5 max-w-3xl text-xl font-semibold leading-8 text-orange-200 md:text-2xl">
            {{ campaign.subtitle }}
          </p>

          <p class="mt-6 max-w-3xl text-base leading-8 text-white/78 md:text-lg">
            {{ campaign.description }}
          </p>

          <div class="mt-8 grid gap-4 sm:grid-cols-3">
            <article
              v-for="item in highlights"
              :key="item.title"
              class="rounded-[28px] border border-white/10 bg-white/8 px-5 py-5 backdrop-blur"
            >
              <div class="text-sm font-black tracking-[0.3em] text-orange-300">{{ item.icon }}</div>
              <h2 class="mt-3 text-xl font-black">{{ item.title }}</h2>
              <p class="mt-2 text-sm leading-7 text-white/70">{{ item.desc }}</p>
            </article>
          </div>
        </div>

        <div class="relative z-10">
          <div class="overflow-hidden rounded-[34px] border border-white/10 bg-white/95 text-[#111827] shadow-[0_30px_80px_rgba(0,0,0,0.28)]">
            <img :src="featureSections[0].image" :alt="campaign.title" class="h-[300px] w-full object-cover md:h-[360px]" />

            <div class="space-y-6 p-6 md:p-8">
              <div>
                <div class="text-sm font-semibold tracking-[0.28em] text-orange-500">LIMITED EARLY BIRD</div>
                <div class="mt-3 flex items-end gap-3">
                  <span class="text-5xl font-black text-orange-500">{{ campaign.fundingPercent }}%</span>
                  <span class="pb-2 text-sm text-slate-500">目標達成</span>
                </div>
                <div class="mt-4 h-3 overflow-hidden rounded-full bg-slate-200">
                  <div class="h-full rounded-full bg-gradient-to-r from-orange-500 to-amber-300" :style="{ width: progressWidth }" />
                </div>
              </div>

              <div class="grid grid-cols-2 gap-4 rounded-[24px] bg-[#f8fafc] p-5">
                <div>
                  <div class="text-sm text-slate-500">累計金額</div>
                  <div class="mt-1 text-2xl font-black">NT$ {{ formatPrice(campaign.fundedAmount) }}</div>
                </div>
                <div>
                  <div class="text-sm text-slate-500">支持人數</div>
                  <div class="mt-1 text-2xl font-black">{{ formatPrice(campaign.supporters) }} 人</div>
                </div>
                <div>
                  <div class="text-sm text-slate-500">募資目標</div>
                  <div class="mt-1 text-xl font-bold">NT$ {{ formatPrice(campaign.goal) }}</div>
                </div>
                <div>
                  <div class="text-sm text-slate-500">剩餘時間</div>
                  <div class="mt-1 text-xl font-bold">{{ campaign.daysLeft }} 天</div>
                </div>
              </div>

              <div class="rounded-[28px] bg-[#111827] p-6 text-white">
                <div class="inline-flex rounded-full bg-orange-500/15 px-3 py-1 text-xs font-bold tracking-[0.18em] text-orange-300">
                  超早鳥方案
                </div>

                <div class="mt-4 flex flex-wrap items-end gap-3">
                  <span class="text-4xl font-black text-orange-400">NT$ {{ formatPrice(campaign.earlyBirdPrice) }}</span>
                  <span class="text-lg text-white/35 line-through">NT$ {{ formatPrice(campaign.originalPrice) }}</span>
                </div>

                <p class="mt-3 text-sm leading-7 text-white/70">
                  現省 NT$ {{ formatPrice(savings) }}。適合想一次補齊常用工具、又不想買到太重太雜的人。
                </p>

                <div class="mt-5 grid gap-3 sm:grid-cols-2">
                  <button class="rounded-2xl bg-orange-500 px-5 py-4 text-base font-black text-white transition hover:bg-orange-400">
                    立即支持專案
                  </button>
                  <button class="rounded-2xl border border-white/15 px-5 py-4 text-base font-bold text-white transition hover:border-orange-400 hover:text-orange-300">
                    加入收藏清單
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="grid gap-6 lg:grid-cols-2">
        <article
          v-for="item in storyBlocks"
          :key="item.title"
          class="rounded-[32px] bg-white p-8 shadow-[0_16px_50px_rgba(15,23,42,0.06)]"
        >
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">{{ item.kicker }}</p>
          <h2 class="mt-4 text-3xl font-black leading-tight">{{ item.title }}</h2>
          <p class="mt-5 text-base leading-8 text-slate-600">{{ item.content }}</p>
        </article>
      </div>
    </section>

    <section
      v-for="(section, index) in featureSections"
      :id="section.id"
      :key="section.id"
      :class="index % 2 === 0 ? 'bg-[#151515] text-white' : 'bg-white text-[#111827]'"
    >
      <div
        class="mx-auto grid max-w-7xl items-center gap-10 px-4 py-16 lg:px-8"
        :class="index % 2 === 0 ? 'lg:grid-cols-[1fr_1.05fr]' : 'lg:grid-cols-[1.05fr_1fr]'"
      >
        <div :class="index % 2 !== 0 ? 'order-2 lg:order-1' : ''">
          <p class="text-sm font-bold uppercase tracking-[0.3em]" :class="index % 2 === 0 ? 'text-orange-400' : 'text-orange-500'">
            {{ section.kicker }}
          </p>
          <h2 class="mt-4 text-4xl font-black leading-tight md:text-5xl">{{ section.title }}</h2>
          <p class="mt-6 text-base leading-8" :class="index % 2 === 0 ? 'text-white/72' : 'text-slate-600'">
            {{ section.body }}
          </p>
          <ul class="mt-8 space-y-4">
            <li
              v-for="item in section.bullets"
              :key="item"
              class="flex items-start gap-3 text-base leading-7"
              :class="index % 2 === 0 ? 'text-white/85' : 'text-slate-700'"
            >
              <span class="mt-2 h-2.5 w-2.5 rounded-full bg-orange-400" />
              <span>{{ item }}</span>
            </li>
          </ul>
        </div>

        <div :class="index % 2 !== 0 ? 'order-1 lg:order-2' : ''">
          <div class="overflow-hidden rounded-[34px] border border-black/5 shadow-[0_16px_60px_rgba(15,23,42,0.14)]">
            <img :src="section.image" :alt="section.title" class="w-full object-cover" />
          </div>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="mb-10 text-center">
        <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">動態示意</p>
        <h2 class="mt-3 text-4xl font-black">像 GIF 一樣快速理解工具怎麼幫你省動作</h2>
      </div>

      <div class="grid gap-6 lg:grid-cols-3">
        <article
          v-for="item in motionDemos"
          :key="item.title"
          class="rounded-[30px] bg-white p-5 shadow-[0_16px_50px_rgba(15,23,42,0.06)]"
        >
          <div v-html="item.motionSvg" />
          <h3 class="mt-5 text-2xl font-black">{{ item.title }}</h3>
          <p class="mt-3 text-sm leading-7 text-slate-600">{{ item.desc }}</p>
        </article>
      </div>
    </section>

    <section class="bg-white py-16">
      <div class="mx-auto max-w-7xl px-4 lg:px-8">
        <div class="mb-10 text-center">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">Use Case</p>
          <h2 class="mt-3 text-4xl font-black">不是只為一種工作設計，而是為日常高頻維修設計</h2>
        </div>

        <div class="grid gap-6 md:grid-cols-2 xl:grid-cols-4">
          <article
            v-for="item in useScenarios"
            :key="item.title"
            class="overflow-hidden rounded-[30px] bg-[#101828] text-white shadow-[0_20px_50px_rgba(15,23,42,0.12)]"
          >
            <img :src="item.image" :alt="item.title" class="w-full object-cover" />
            <div class="p-6">
              <h3 class="text-2xl font-black">{{ item.title }}</h3>
              <p class="mt-3 text-sm leading-7 text-white/72">{{ item.desc }}</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="mb-8 text-center">
        <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">Comparison</p>
        <h2 class="mt-3 text-4xl font-black">你買的不只是工具數量，而是整體使用節奏</h2>
      </div>

      <div class="overflow-hidden rounded-[30px] bg-white shadow-[0_16px_50px_rgba(15,23,42,0.06)]">
        <div class="overflow-x-auto">
          <table class="min-w-full border-collapse text-left">
            <thead>
              <tr class="bg-[#0f172a] text-white">
                <th class="px-6 py-5 text-sm font-black">比較項目</th>
                <th class="px-6 py-5 text-sm font-black text-orange-300">ForgeMax M24</th>
                <th class="px-6 py-5 text-sm font-black">一般工具組</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="row in comparisonRows" :key="row.label" class="border-t border-slate-200">
                <td class="px-6 py-5 font-bold">{{ row.label }}</td>
                <td class="px-6 py-5 text-slate-700">{{ row.pro }}</td>
                <td class="px-6 py-5 text-slate-500">{{ row.normal }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <section class="bg-[#111111] py-16 text-white">
      <div class="mx-auto grid max-w-7xl gap-8 px-4 lg:grid-cols-[1.2fr_0.8fr] lg:px-8">
        <div class="overflow-hidden rounded-[32px] border border-white/10 shadow-[0_18px_60px_rgba(0,0,0,0.25)]">
          <div class="aspect-video w-full">
            <iframe
              class="h-full w-full"
              src="https://www.youtube.com/embed/m0JyMQ7CAVU"
              title="33 in 1 Precision screwdriver & socket set Review by Rea"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              allowfullscreen
            />
          </div>
        </div>

        <div class="flex flex-col justify-center">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-400">YouTube Review</p>
          <h2 class="mt-3 text-4xl font-black leading-tight">
            真正拿來工作的工具，
            <br>
            看使用節奏最準
          </h2>
          <p class="mt-5 text-base leading-8 text-white/72">
            這段 YouTube 影片展示的是多功能螺絲起子與套筒工具組的實際操作節奏，很適合放在商品頁中段，
            讓使用者直接感受到「切換規格、連續施力、快速收納」這類手工具頁最重要的體感資訊。
          </p>
          <a
            href="https://www.youtube.com/watch?v=m0JyMQ7CAVU"
            target="_blank"
            rel="noreferrer"
            class="mt-6 inline-flex w-fit rounded-2xl bg-white px-5 py-4 font-bold text-black transition hover:bg-orange-500 hover:text-white"
          >
            開啟 YouTube 觀看
          </a>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="mb-10 text-center">
        <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">In The Box</p>
        <h2 class="mt-3 text-4xl font-black">一盒裡，剛好就是你最常用的那一組</h2>
      </div>

      <div class="grid gap-5 sm:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="item in boxItems"
          :key="`${item.name}-${item.qty}`"
          class="rounded-[30px] bg-white p-5 shadow-[0_16px_50px_rgba(15,23,42,0.06)]"
        >
          <div class="overflow-hidden rounded-[24px]">
            <img :src="item.image" :alt="item.name" class="w-full object-cover" />
          </div>
          <div class="mt-5 flex items-start justify-between gap-4">
            <h3 class="text-xl font-black">{{ item.name }}</h3>
            <span class="rounded-full bg-orange-100 px-3 py-1 text-sm font-bold text-orange-600">{{ item.qty }}</span>
          </div>
        </article>
      </div>
    </section>

    <section class="bg-white py-16">
      <div class="mx-auto max-w-7xl px-4 lg:px-8">
        <div class="mb-10 text-center">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">Material & Finish</p>
          <h2 class="mt-3 text-4xl font-black">從材質到收納，都在幫使用體驗加分</h2>
        </div>

        <div class="grid gap-6 md:grid-cols-2 xl:grid-cols-4">
          <article
            v-for="item in materials"
            :key="item.title"
            class="rounded-[30px] bg-[#111827] p-6 text-white shadow-[0_16px_50px_rgba(15,23,42,0.1)]"
          >
            <div class="mb-5 h-14 w-14 rounded-2xl bg-orange-500/15" />
            <h3 class="text-2xl font-black">{{ item.title }}</h3>
            <p class="mt-4 text-sm leading-7 text-white/72">{{ item.desc }}</p>
          </article>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="grid gap-6 lg:grid-cols-2">
        <article class="rounded-[32px] bg-white p-8 shadow-[0_16px_50px_rgba(15,23,42,0.06)]">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">Specification</p>
          <h2 class="mt-3 text-3xl font-black">規格資訊</h2>

          <div class="mt-8 space-y-4">
            <div
              v-for="item in specs"
              :key="item.label"
              class="flex items-start justify-between gap-4 border-b border-slate-200 pb-4"
            >
              <div class="font-bold text-slate-500">{{ item.label }}</div>
              <div class="text-right font-semibold">{{ item.value }}</div>
            </div>
          </div>
        </article>

        <article class="rounded-[32px] bg-[#111827] p-8 text-white shadow-[0_16px_50px_rgba(15,23,42,0.06)]">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-300">Who Is It For</p>
          <h2 class="mt-3 text-3xl font-black">適合這樣的你</h2>

          <div class="mt-8 grid gap-4 sm:grid-cols-2">
            <div class="rounded-[24px] bg-white/8 px-5 py-5 text-center text-lg font-bold">常自己組家具的人</div>
            <div class="rounded-[24px] bg-white/8 px-5 py-5 text-center text-lg font-bold">想整理工作桌的人</div>
            <div class="rounded-[24px] bg-white/8 px-5 py-5 text-center text-lg font-bold">有腳踏車或車庫維護需求</div>
            <div class="rounded-[24px] bg-white/8 px-5 py-5 text-center text-lg font-bold">不想買一堆但想買對的人</div>
          </div>
        </article>
      </div>
    </section>

    <section class="bg-white py-16">
      <div class="mx-auto max-w-7xl px-4 lg:px-8">
        <div class="mb-10 text-center">
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">Real Feedback</p>
          <h2 class="mt-3 text-4xl font-black">先被收納吸引，最後離不開的是順手度</h2>
        </div>

        <div class="grid gap-6 lg:grid-cols-3">
          <article
            v-for="item in testimonials"
            :key="item.name"
            class="rounded-[30px] bg-[#fafaf8] p-8 shadow-[0_16px_50px_rgba(15,23,42,0.04)]"
          >
            <div class="text-5xl font-black text-orange-400">“</div>
            <p class="mt-4 text-base leading-8 text-slate-700">{{ item.text }}</p>
            <div class="mt-6">
              <div class="text-lg font-black">{{ item.name }}</div>
              <div class="text-sm text-slate-500">{{ item.role }}</div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="mx-auto max-w-7xl px-4 py-16 lg:px-8">
      <div class="mb-10 text-center">
        <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-500">FAQ</p>
        <h2 class="mt-3 text-4xl font-black">常見問題</h2>
      </div>

      <div class="space-y-4">
        <article
          v-for="(item, index) in faqs"
          :key="item.q"
          class="overflow-hidden rounded-[28px] bg-white shadow-[0_16px_50px_rgba(15,23,42,0.05)]"
        >
          <button class="flex w-full items-center justify-between gap-4 px-6 py-5 text-left" @click="toggleFaq(index)">
            <span class="text-lg font-black">{{ item.q }}</span>
            <span class="text-2xl font-bold text-orange-500">{{ item.open ? '−' : '+' }}</span>
          </button>
          <div v-show="item.open" class="border-t border-slate-200 px-6 py-5 text-base leading-8 text-slate-600">
            {{ item.a }}
          </div>
        </article>
      </div>
    </section>

    <section class="relative overflow-hidden bg-[#111111] py-16 text-white">
      <div class="hero-glow hero-glow-left" />
      <div class="hero-glow hero-glow-right" />

      <div class="relative mx-auto grid max-w-7xl items-center gap-8 px-4 lg:grid-cols-[1fr_0.92fr] lg:px-8">
        <div>
          <p class="text-sm font-bold uppercase tracking-[0.3em] text-orange-400">Final Call</p>
          <h2 class="mt-4 text-4xl font-black leading-tight md:text-5xl">
            如果你想找的是一套
            <br>
            真的會一直拿出來用的工具
          </h2>
          <p class="mt-6 max-w-2xl text-base leading-8 text-white/72">
            ForgeMax M24 不靠花俏功能堆滿頁面，它真正想做的是讓你在每一次鎖付、拆裝與整理裡，都少一點多餘動作，多一點順手與俐落。
            從拆箱那刻開始，你就會知道這不是臨時買來頂著用的工具，而是一套能長期待在生活裡、被反覆信任的工具。
          </p>

          <div class="mt-8 flex flex-wrap items-end gap-4">
            <span class="rounded-full bg-orange-500/15 px-3 py-1 text-xs font-bold tracking-[0.18em] text-orange-300">
              募資限定優惠
            </span>
            <span class="text-5xl font-black text-orange-400">NT$ {{ formatPrice(campaign.earlyBirdPrice) }}</span>
            <span class="text-xl text-white/35 line-through">NT$ {{ formatPrice(campaign.originalPrice) }}</span>
          </div>

          <div class="mt-8 flex flex-wrap gap-4">
            <button class="rounded-2xl bg-orange-500 px-6 py-4 text-base font-black text-white transition hover:bg-orange-400">
              立即支持 ForgeMax
            </button>
            <button class="rounded-2xl border border-white/15 px-6 py-4 text-base font-black text-white transition hover:border-orange-400 hover:text-orange-300">
              下載規格資訊
            </button>
          </div>
        </div>

        <div class="overflow-hidden rounded-[34px] border border-white/10 shadow-[0_20px_70px_rgba(0,0,0,0.28)]">
          <img
            :src="createPhotoSvg({ title: 'READY FOR DAILY REPAIR', subtitle: '從家裡到工作桌都很有存在感', accent: '#fb923c', secondary: '#111827', background: '#ece7df' })"
            alt="ForgeMax final visual"
            class="w-full object-cover"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.detail-page {
  scroll-behavior: smooth;
}

.hero-section,
.detail-page section {
  position: relative;
}

.hero-glow {
  position: absolute;
  width: 28rem;
  height: 28rem;
  border-radius: 9999px;
  filter: blur(70px);
  pointer-events: none;
}

.hero-glow-left {
  top: -8rem;
  left: -8rem;
  background: rgba(249, 115, 22, 0.16);
}

.hero-glow-right {
  right: -8rem;
  bottom: -8rem;
  background: rgba(14, 165, 233, 0.14);
}

:deep(.motion-svg) {
  width: 100%;
  height: auto;
  display: block;
}
</style>
