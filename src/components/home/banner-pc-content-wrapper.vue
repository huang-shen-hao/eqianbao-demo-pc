<script lang="ts" setup="">
import { ref } from 'vue';

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
// 轮播图change事件
const carouselRef = ref();
let currentIndex = ref<number>(0);
const imageChange = (index: number) => {
  // console.log('oooo', index);
  currentIndex.value = index; // 记录当前index
};
const onBtnChange = (index: number) => {
  carouselRef.value && carouselRef.value.setActiveItem(index);
};

const buttonList = ['免费试用', '了解详情', '了解更多', '了解更多', '了解更多'];
const titleList = [
  {
    title: '签合同，用e签宝',
    context: '电子合同签管一体化平台',
  },
  {
    title: '市占持续领先，稳占第一',
    context:
      '根据权威智库机构IDC发布的《2023H1中国电子签名报告》，2023年上半年， e签宝在公有云、本地化部署、电签行业市占率持续第一',
  },
  {
    title: 'e签宝个人合伙人计划',
    context: '成为个人合伙人，共享数字化转型红利',
  },
  {
    title: '统一印章管理平台',
    context: '系统本地部署，隐私数据安全，符合信创要求',
  },
  {
    title: 'OFD电子保函解决方案',
    context: '追加文件已有签章不失效，支持信创/非信创环境',
  },
];
const bottomList = [
  {
    title: '助力企业异地签约用印',
    url: 'https://www.esign.cn/upload/resources/image/2022/05/17/32870.png',
    context: '点击免费开启签约体验',
  },
  {
    title: '荣获胡润、福布斯等权威大奖',
    url: 'https://www.esign.cn/upload/resources/image/2022/05/17/32869.png',
    context: '持续引领中国电子签名行业发展',
  },
  {
    title: '立即对接业务系统',
    url: 'https://www.esign.cn/upload/resources/image/2022/05/17/32871.png',
    context: '在自己的业务系统集成电子签名',
  },
  {
    title: 'IDC:三个第一 全面领跑',
    url: 'https://www.esign.cn/upload/resources/image/2022/12/12/34913_120x120.png',
    context: 'e签宝在公有云、本地化部署、电签行业市占均为第一',
  },
];
const hotUrl =
  'https://trial-cdn.esign.cn/upload/dbc3e6d6-819c-5ef0-8b25-9ef4c2da1b6e!!5-16.png';
</script>

<template>
  <div class="container">
    <!--轮播图-->
    <el-carousel
      ref="carouselRef"
      height="400px"
      :autoplay="true"
      :interval="6000"
      trigger="click"
      @change="imageChange"
    >
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
          :style="{ 'background-image': `url(${item.url})` }"
        ></div>
      </el-carousel-item>
    </el-carousel>
    <!--自定义的轮播图指示器按钮-->
    <div class="pagination_container">
      <div
        :class="{
          pagination_container_item: true,
          pagination_container_item_select: currentIndex === index,
        }"
        v-for="(item, index) in imgList.length + 1"
        :key="item"
        @click="onBtnChange(index)"
      ></div>
    </div>
    <!--文字描述-->
    <div class="info_container">
      <!--title-->
      <div class="title" v-for="(item, index) in titleList" :key="index">
        <template v-if="currentIndex == index">
          <p class="title_top">{{ item.title }}</p>
          <p class="title_bottom">{{ item.context }}</p>
        </template>
      </div>
      <!--自定义的跳转按钮-->
      <div class="btn" v-for="(item, index) in buttonList" :key="index">
        <el-button class="centerButton" v-if="currentIndex === index">
          {{ item }}
        </el-button>
      </div>
    </div>
    <!--底部的信息-->
    <div class="bottom">
      <div v-for="(item, index) in bottomList" :key="index" class="bottom_item">
        <!--左侧图片-->
        <div class="bottom_item_left">
          <img :src="item.url" width="60px" height="60px" />
        </div>
        <!--右侧文字-->
        <div class="bottom_item_right">
          <p class="p1">{{ item.title }}</p>
          <p class="p2">{{ item.context }}</p>
          <div class="hot" v-if="index === 0">
            <img :src="hotUrl" width="25px" height="18px" />
          </div>
          <div class="hot" v-if="index === 3">
            <img :src="hotUrl" width="25px" height="18px" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  margin-top: 111px; //美观
  position: relative;
  .el-carousel {
    .carousel_img_item {
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center center;
      width: 100%;
      height: 100%;
    }
  }
  .pagination_container {
    height: 4px;
    display: flex;
    position: absolute;
    top: 80%;
    left: 4%;
    .pagination_container_item {
      height: 100%;
      width: 50px;
      background-color: #ded8d8;
      margin: 0 4px;
    }
    .pagination_container_item:hover {
      cursor: pointer;
    }
    //选中的样式变化
    .pagination_container_item_select {
      height: 100%;
      width: 50px;
      background-color: #676262;
      animation: LeftToRight 6s;
      transform-origin: left;
    }
    @keyframes LeftToRight {
      from {
        transform: scaleX(0);
      }
      to {
        transform: scaleX(1);
      }
    }
  }
  .info_container {
    position: relative;
    position: absolute;
    width: 80%;
    height: 320px;
    //background-color: #666666;
    top: -10%;
    .btn {
      position: absolute;
      bottom: 0;
      left: 5%;
      .centerButton {
        width: 159px;
        height: 44px;
        line-height: 44px;
        text-align: center;
        background: #c00;
        border-radius: 4px;
        cursor: pointer;
        text-decoration: none;
        color: #fff;
      }
    }
    .title {
      position: absolute;
      top: 0;
      left: 5%;
      width: 60%;
      .title_top {
        font-size: 52px;
        font-weight: 600;
        line-height: 73px;
        color: rgba(0, 0, 0, 0.85);
        margin-bottom: 16px;
      }
      .title_bottom {
        font-size: 18px;
        font-weight: 400;
        line-height: 25px;
        color: rgba(0, 0, 0, 0.65);
        margin-bottom: 46px;
      }
    }
  }
  .bottom {
    position: absolute;
    bottom: -15%;
    width: 100%;
    height: 100px;
    background-color: rgba(250, 250, 250, 0.8);
    display: flex;
    .bottom_item {
      height: 100%;
      min-width: 20%;
      display: flex;
      .bottom_item_left {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 8px;
      }
      .bottom_item_right {
        position: relative;
        .hot {
          position: absolute;
          top: 0;
          left: 160px;
        }
        .p1 {
          line-height: 22px;
          font-size: 16px;
          font-weight: 600;
          text-overflow: ellipsis;
          color: rgba(0, 0, 0, 0.85);
          position: relative;
        }
        .p2 {
          line-height: 20px;
          font-size: 14px;
          font-weight: 400;
          white-space: nowrap;
          text-overflow: ellipsis;
          color: rgba(0, 0, 0, 0.65);
          margin-top: 4px;
        }
      }
    }
  }
}
//不需要
::v-deep .el-carousel__indicators {
  display: none;
}
::v-deep .el-carousel__arrow {
  display: none;
}
</style>
