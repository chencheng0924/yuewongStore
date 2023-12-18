<script setup>
import { onMounted, reactive, computed, ref, onUnmounted } from 'vue'
import { getAssetsFile } from '@/utils/commonUse'
const props = defineProps({
  picList: {
    type: Array,
    default: []
  },
  ifCarousel: {
    type: Boolean,
    default: true
  },
  gridArea: {  // grid排版方式
    type: String,
    default: ''
  },
  ifOverflowScroll: {
    type: Boolean,
    default: false
  }
})
const emit = defineEmits(['openPic'])
const open = (idx) => {
  emit('openPic', idx)
}
</script>
<template>
  <div class="grid gap-2 gridContent w-full" :class="{'overflow-x-scroll': props.ifOverflowScroll}" :style="{ 'grid-template-areas': props.gridArea }">
    <div v-for="(it, idx) in props.picList" :style="{ 'gridArea': it.imgName, width: it.w + 'px', height: it.h + 'px'  }" :key="idx" class="rounded-xl cursor-pointer" @click="open(idx)">
      <!-- <img :src="getAssetsFile(it.imgName + '.png')" alt="" class="rounded-xl hover:opacity-[85%] h-[30px]" :class="[`min-h-[${it.height}px]`]"> -->
      <img :src="getAssetsFile(it.imgName + '.png')" alt="" class="rounded-xl hover:opacity-[85%] w-full h-full object-cover">
      <!-- <img :src="getAssetsFile(it.imgName + '.png')" alt="" class="rounded-xl hover:opacity-[85%] min-h-[300px]"> -->
    </div>
  </div>
</template>
<style lang="scss" scoped>

</style>