<script lang="ts" setup="">
const videoUrl =
  'https://www.esign.cn/upload/resources/file/2023/06/30/35388.mp4';

const imgList = [
  {
    url: 'https://www.esign.cn/upload/resources/file/2023/12/26/40761.jpg',
  },
  {
    url: 'https://www.esign.cn/upload/resources/file/2023/06/09/35321.png',
  },
  {
    url: 'https://www.esign.cn/upload/resources/file/2023/05/15/35311.png',
  },
  {
    url: 'https://www.esign.cn/upload/resources/file/2022/11/01/34789.png',
  },
];
</script>

<template>
  <div class="container">
    <!--轮播图-->
    <el-carousel height="400px" :autoplay="false" trigger="click">
      <!--第一个是视频-->
      <el-carousel-item style="display: block">
        <video
          :src="videoUrl"
          :autoplay="true"
          :muted="true"
          :loop="true"
          style="width: 100%; height: 100%; object-fit: cover"
        ></video>
      </el-carousel-item>
      <!--后面四个是图片-->
      <el-carousel-item
        class="el-carousel-item_img"
        style="display: block"
        v-for="(item, index) in imgList"
        :key="index"
      >
        <div
          class="carousel_img_item"
          :style="{ backgroundImage: `url(${item.url})` }"
        ></div>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  margin-top: 4px; //美观
  .el-carousel {
    .carousel_img_item {
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center center;
      width: 100%;
      height: 100%;
    }
  }
}
</style>
