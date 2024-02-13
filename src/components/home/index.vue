<script setup lang="ts">
import TabBar from '@/components/home/tabBar.vue';
import bannerWrapper from '@/components/home/banner-pc-content-wrapper.vue';
import Product from '@/components/home/product.vue';
import Plan from '@/components/home/solve-plan-wrapper.vue';
import Infrastructure from '@/components/home/infrastructure.vue';
import Choose from '@/components/home/choose.vue';
</script>

<template>
  <div class="container">
    <!--  顶部标签栏-->
    <tab-bar />
    <!--轮播图-->
    <bannerWrapper />
    <!--产品介绍-->
    <Product />
    <!--定制化行业解决方案 轮播图-->
    <Plan />
    <!--安全合规的基础设施-->
    <Infrastructure />
    <!--更多客户选择使用e签宝-->
    <Choose />
  </div>
</template>

<style scoped lang="scss"></style>
