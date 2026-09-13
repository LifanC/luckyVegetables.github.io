<script setup>
import bunImage from '../../img/a.jpg'
import noodleImage from '../../img/b.jpg'

defineProps({ bowl: Boolean })
</script>

<template>
  <img
    class="bun-art"
    :src="bowl ? noodleImage : bunImage"
    :alt="bowl ? '素食麵線' : '金黃素食水煎包'"
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
