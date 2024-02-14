<script lang="ts" setup="">
import { onMounted, ref } from 'vue';

const infoImgList = [
  {
    url: 'https://www.esign.cn/upload/resources/image/2023/12/28/40775.jpg',
    text: '年终盘点：致2023，一图看e签宝电子合同的成长瞬间',
  },
  {
    url: 'https://www.esign.cn/upload/resources/image/2023/09/15/39474.jpeg',
    text: '精彩纷呈!e签宝第二届用户生态峰会重磅推出ePaaS+电子合同签管一体化两大平台',
  },
  {
    url: 'https://www.esign.cn/upload/resources/image/2023/09/12/39458.jpeg',
    text: 'e签宝亮相“2023 Cloud 100 China”，荣获“生产力及协作”领域排名第一电子签名SaaS服务商',
  },
];
// 记录当前index
const currentIndex = ref<number>(0);
const paginationRef = ref(); //轮播图指示器
const onImgChange = (e: any) => {
  console.log('change');
  currentIndex.value = e;
  console.log(paginationRef.value);
  if (paginationRef.value[currentIndex.value]) {
    paginationRef.value[currentIndex.value].classList.add('active'); //动态添加类
  }
  let arr = [0, 1, 2].filter((item) => item !== currentIndex.value);
  arr.forEach((item) => {
    if (paginationRef.value[item]) {
      paginationRef.value[item].classList.remove('active'); //排他
    }
  });
};
const carouselRef = ref();
let autoplay = ref<boolean>(true);
const onBtnClick = (index: number) => {
  console.log(carouselRef.value);
  carouselRef.value && carouselRef.value.setActiveItem(index);
};
onMounted(() => {
  onImgChange(0);
});
</script>

<template>
  <div class="info-container">
    <p class="info-container-title">资讯内容</p>
    <div class="info-container-main">
      <div class="info-container-main-left">
        <el-carousel
          :autoplay="autoplay"
          ref="carouselRef"
          height="332px"
          @change="onImgChange"
          class="test"
        >
          <el-carousel-item
            style="display: block"
            v-for="(item, index) in infoImgList"
            :key="index"
          >
            <img :src="item.url" width="100%" height="100%" />
          </el-carousel-item>
        </el-carousel>
        <div class="info-container-main-left-text">
          {{ infoImgList[currentIndex].text }}
        </div>
        <!--自定义按钮-->
        <div class="left-pagination">
          <div
            ref="paginationRef"
            class="left-pagination-item"
            v-for="(item, index) in infoImgList.length"
            :key="index"
            @click="onBtnClick(index)"
          ></div>
        </div>
      </div>
      <div class="info-container-main-right"></div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.info-container {
  width: 100%;

  background: url('https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/info-bg.a064ff0.jpg')
    no-repeat 50% center;
  background-size: cover;
  padding: 20px;
  box-sizing: border-box;
  .info-container-title {
    text-align: center;
    height: 50px;
    font-size: 32px;
    font-weight: 600;
    color: rgba(0, 0, 0, 0.85);
    line-height: 50px;
  }
  .info-container-main {
    width: 100%;
    height: 418px;
    background-color: #676262;
    .info-container-main-left {
      width: 40%;
      height: 332px;
      .info-container-main-left-text {
        width: 100%;
        height: 68px;
        box-sizing: border-box;
        background: #fff;
        padding-left: 30px;
        box-shadow: 0 2px 10px 0 hsla(0, 0, 88.2%, 0.5);
        cursor: pointer;
        text-align: center;
        font-size: 20px;
        line-height: 68px;
        white-space: nowrap;
        overflow: hidden; /* 隐藏溢出的内容 */
        text-overflow: ellipsis; /* 文本溢出时显示省略号 */
      }
      .left-pagination {
        width: 100%;
        height: 18px;
        display: flex;
        justify-content: center;
        align-items: center;
        .left-pagination-item {
          height: 8px;
          width: 8px;
          background-color: rgba(234, 226, 234, 0.9);
          margin: 0 4px;
        }
        .left-pagination-item:hover {
          background-color: rgba(152, 146, 152, 0.9);
          cursor: pointer;
        }
        .left-pagination-item.active {
          background-color: rgba(152, 146, 152, 0.9);
        }
      }
    }
  }
  ::v-deep .el-carousel__indicators {
    display: none;
  }
}
</style>
