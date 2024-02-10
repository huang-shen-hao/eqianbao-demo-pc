<script setup lang="ts">
import TabBar from '@/components/home/tabBar.vue';
import Swiper from '@/components/home/swiper.vue';
import Product from '@/components/home/product.vue';
</script>

<template>
  <div class="container">
    <!--  顶部标签栏-->
    <tab-bar />
    <!--轮播图-->
    <Swiper />
    <!--产品介绍-->
    <Product />
  </div>
</template>

<style scoped lang="scss"></style>
