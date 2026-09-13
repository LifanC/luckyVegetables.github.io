<script setup>
defineProps({ bowl: Boolean })
</script>

<template>
  <svg v-if="!bowl" viewBox="0 0 620 490" role="img" aria-label="金黃色水煎包與綠葉插畫">
    <defs>
      <radialGradient id="dough">
        <stop stop-color="#fff9e5" />
        <stop offset=".72" stop-color="#f1d9a7" />
        <stop offset="1" stop-color="#c9904c" />
      </radialGradient>
      <linearGradient id="crust" x2="0" y2="1">
        <stop stop-color="#e4b66d" />
        <stop offset="1" stop-color="#ad632f" />
      </linearGradient>
      <filter id="shadow">
        <feGaussianBlur stdDeviation="10" />
      </filter>
      <g id="bun">
        <ellipse cy="38" rx="99" ry="57" fill="#533720" opacity=".15" filter="url(#shadow)" />
        <path d="M-95 6C-104 69-52 88 0 86S104 62 96 8Z" fill="url(#crust)" />
        <ellipse rx="99" ry="66" fill="url(#dough)" />
        <g fill="none" stroke="#d5b47e" stroke-width="2.5" opacity=".7">
          <path
            d="M0-25Q-53-29-73 9M0-25Q-36-44-61-25M0-25Q-11-57-25-52M0-25Q15-53 31-49M0-25Q52-40 70-17M0-25Q64-10 77 21M0-25Q39 1 36 44M0-25Q9 8-5 45M0-25Q-23 6-45 29" />
        </g>
        <ellipse cy="-25" rx="13" ry="7" fill="#d9bd8c" />
        <g fill="#a66b30" opacity=".5">
          <ellipse cx="-56" cy="55" rx="5" ry="2" />
          <ellipse cx="32" cy="63" rx="8" ry="2" />
          <ellipse cx="58" cy="51" rx="4" ry="2" />
        </g>
      </g>
    </defs>
    <ellipse cx="313" cy="381" rx="242" ry="55" fill="#544c34" opacity=".12" filter="url(#shadow)" />
    <ellipse cx="308" cy="315" rx="262" ry="132" fill="#d8d3b6" />
    <ellipse cx="308" cy="303" rx="262" ry="127" fill="#f9f4df" />
    <ellipse cx="308" cy="304" rx="234" ry="108" fill="none" stroke="#b0ba99" stroke-width="2" />
    <ellipse cx="308" cy="303" rx="210" ry="91" fill="#e6e6c9" />
    <g fill="#6b8850">
      <path d="M100 308Q20 215 127 203Q148 254 100 308" />
      <path d="M105 318Q26 311 55 265Q109 264 105 318" />
      <path d="M447 288Q483 182 529 229Q508 285 447 288" />
      <path d="M454 290Q545 258 544 308Q492 330 454 290" />
    </g>
    <use href="#bun" transform="translate(235 227) rotate(-12) scale(.95)" />
    <use href="#bun" transform="translate(397 248) rotate(15) scale(.92)" />
    <use href="#bun" transform="translate(286 332) scale(1.08)" />
    <g stroke="#fbf6e9" stroke-width="6" fill="none" stroke-linecap="round" opacity=".9">
      <path d="M249 123Q228 97 251 76Q268 59 254 39" />
      <path d="M306 115Q285 91 308 64Q321 46 312 28" />
      <path d="M363 132Q348 111 366 91" />
    </g>
  </svg>
  <svg v-else viewBox="0 0 620 490" role="img" aria-label="溫暖素食麵線插畫">
    <ellipse cx="310" cy="402" rx="182" ry="22" fill="#284b39" opacity=".1" />
    <path d="M111 233Q128 410 310 412Q491 405 509 233Z" fill="#ebe1c9" />
    <path d="M145 279Q169 370 270 389" fill="none" stroke="#fff8e8" stroke-width="12" />
    <ellipse cx="310" cy="234" rx="201" ry="89" fill="#fffaeb" />
    <ellipse cx="310" cy="234" rx="178" ry="70" fill="#a87040" />
    <g fill="none" stroke="#e6c591" stroke-width="5">
      <path v-for="i in 9" :key="i" :d="`M${165 + i * 8} ${204 + i * 7} Q280 ${145 + i * 13} 390 ${200 + i * 7} T440 ${225 + i * 4}`" />
    </g>
    <g fill="#567a43">
      <ellipse cx="300" cy="201" rx="28" ry="13" transform="rotate(-30 300 201)" />
      <ellipse cx="340" cy="206" rx="28" ry="12" transform="rotate(30 340 206)" />
      <ellipse cx="321" cy="182" rx="12" ry="26" />
    </g>
    <g stroke="#faf4e5" stroke-width="6" fill="none" stroke-linecap="round">
      <path d="M260 120Q240 95 263 72" />
      <path d="M318 110Q295 85 321 53" />
      <path d="M373 122Q353 99 373 78" />
    </g>
  </svg>
</template>
