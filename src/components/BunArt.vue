<script setup>
import bunImage from '../../img/a.jpg'
import noodleImage from '../../img/b.jpg'
import zongziImage from '../../img/c.jpg'
import soyMilkImage from '../../img/d.jpg'

defineProps(
  { 
    type: { 
      type: String, 
      default: 'bun' 
    } 
  }
)

const images = {
  bun: { src: bunImage, alt: '金黃素食水煎包' },
  noodle: { src: noodleImage, alt: '素食麵線' },
  zongzi: { src: zongziImage, alt: '素食南部粽' },
  soyMilk: { src: soyMilkImage, alt: '豆漿' }
}
</script>

<template>
  <img
    class="bun-art"
    :src="(images[type] || images.bun).src"
    :alt="(images[type] || images.bun).alt"
    width="590"
    height="443"
  />
</template>

<style scoped>
.bun-art {
  display: block;
  object-fit: cover;
}
</style>
