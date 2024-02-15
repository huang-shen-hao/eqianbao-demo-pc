<script lang="ts" setup="">
import { ref } from 'vue';

const countList = [
  {
    title: '节约纸张数(年度)',
    number: '63.27',
  },
  {
    title: '节约物流成本(年度)',
    number: '316.34',
  },
  {
    title: '减少碳排放量(年度)',
    number: '5.27',
  },
];
const showQr = ref<boolean>(false);
</script>

<template>
  <div class="video-container">
    <div
      style="position: absolute; width: 100%; height: 600px; overflow: hidden"
    >
      <video
        id="video_banner"
        src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/videos/esignIndex-newbattle.4ff2978.mp4"
        :autoplay="true"
        :muted="true"
        :loop="true"
        width="100%"
      ></video>
    </div>
    <div class="video-main">
      <div class="video-main-title">
        <span>让签署更便捷</span>
        <span style="padding-left: 50px">让信任更简单</span>
      </div>
      <div class="video-main-btn">
        <div class="btn">免费试用</div>
      </div>
      <div class="video-main-counter">
        <div
          class="video-main-counter-item"
          v-for="(item, index) in countList"
          :key="index"
        >
          <div class="video-main-counter-item-title">{{ item.title }}</div>
          <div>
            <span class="video-main-counter-item-number">
              {{ item.number }}
            </span>
            <span v-if="index === 0" class="danwei">亿张</span>
            <span v-if="index === 1" class="danwei">亿元</span>
            <span v-if="index === 2" class="danwei">万吨</span>
          </div>
        </div>
      </div>
      <div class="video-main-bottom">
        <span @mouseenter="showQr = true" @mouseleave="showQr = false">
          e签宝公益林
        </span>
      </div>
      <!--展示二维码-->
      <div class="main-qr" v-if="showQr">
        <div style="background-color: white">
          <img
            src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/qr-code.d5a4caa.png"
            width="150px"
            height="150px"
          />
          <span style="text-align: center; display: block">支付宝扫码查看</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.video-container {
  height: 600px;
  width: 100%;
  position: relative;
  .video-main {
    height: 600px;
    width: 100%;
    position: relative;
    .video-main-title {
      position: absolute;
      width: 60%;
      top: 0;
      left: 20%;
      text-align: center;
      font-size: 40px;
      font-weight: 600;
      color: #fff;
      line-height: 70px;
      padding-top: 60px;
      margin-bottom: 30px;
    }
    .video-main-btn {
      width: 100%;
      height: 40px;
      display: flex;
      justify-content: center;
      position: absolute;
      top: 25%;
      .btn {
        background: #e61717;
        border-color: #e61717;
        cursor: pointer;
        width: 120px;
        height: 40px;
        text-align: center;
        line-height: 40px;
        color: white;
      }
    }
    .video-main-counter {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: space-around;
      position: absolute;
      top: 40%;
      .video-main-counter-item {
        .video-main-counter-item-title {
          font-size: 16px;
          font-weight: 400;
          color: #fff;
          line-height: 26px;
          text-align: center;
        }
        .video-main-counter-item-number {
          font-size: 3.2vw;
          color: #fff;
          line-height: 69px;
        }
        .danwei {
          font-size: 2vw;
          color: #fff;
          line-height: 69px;
          margin-left: 20px;
        }
      }
    }
    .video-main-bottom {
      width: 100%;
      height: 50px;
      position: absolute;
      bottom: 10%;
      display: flex;
      justify-content: center;
      color: white;
      span {
        text-align: center;
        line-height: 70px;
        border-bottom: 1px solid white;
      }
      span:hover {
        color: red;
        border-bottom: 1px solid red;
        cursor: default;
      }
    }
    .main-qr {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      width: 100%;
      position: absolute;
      bottom: 15%;
    }
  }
}
</style>
