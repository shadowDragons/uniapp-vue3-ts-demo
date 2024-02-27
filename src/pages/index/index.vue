<script setup lang="ts">
import { ref } from 'vue'
import CustomNavBar from './componets/CustomNavbar.vue'
import CategoryPanel from './componets/CategoryPanel.vue'
import { getHomeBannerAPI, getHomeCategoryAPI } from '@/services/home'
import type { BannerItem, CategoryItem } from '@/types/home'
import { onLoad } from '@dcloudio/uni-app'

const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}

// 获取前台分类数据
const categoryList = ref<CategoryItem[]>([])
const getHomeCategoryData = async () => {
  const res = await getHomeCategoryAPI()
  categoryList.value = res.result
}

onLoad(() => {
  getHomeBannerData()
  getHomeCategoryData()
})
</script>

<template>
  <CustomNavBar />
  <XtxSwiper :list="bannerList" />
  <CategoryPanel :list="categoryList" />
</template>

<style lang="scss">
//
page {
  background-color: #f7f7f7;
}
</style>
