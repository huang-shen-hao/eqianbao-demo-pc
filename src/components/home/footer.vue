<script lang="ts" setup="">
import { ref } from 'vue';

const linkList = [
  '亚太法务联盟',
  '阿里巴巴',
  '蚂蚁金服',
  '钉钉',
  '阿里云',
  '中国人民大学',
  '北京航空航天大学',
  '用友云',
  '华为',
  '呼叫中心',
  '卫瓴',
];
const agreementLinkList = [
  'e签宝服务协议',
  '隐私政策',
  'e签宝服务等级协议',
  '历史版本协议',
];
const footItem = [
  {
    title: '产品服务',
    sub: [
      '签管一体化电子合同云平台',
      '企业统一印章平台',
      '钉钉智能合同',
      '开放服务',
      '身份认证',
    ],
  },
  {
    title: '快速入口',
    sub: ['立即注册', '立即登录', '客服中心', '下载关注'],
  },
  {
    title: '诚邀合作',
    sub: ['渠道合作', '生态合作'],
  },
  {
    title: '关于我们',
    sub: ['公司介绍', '公司动态', '技术资质', '加入我们', '联系我们'],
  },
];
const serveList = [
  {
    name: '客服热线',
    tel: '400-087-8198',
  },
  {
    name: '销售热线',
    tel: '0571-85785223',
  },
  {
    name: '商务合作',
    tel: 'market@esign.cn',
  },
  {
    name: 'CEO直达信箱',
    tel: 'CEO@esign.cn',
  },
];
const iconArr = [
  {
    icon: 'https://www.esign.cn/images/weixinduck.png',
    url: 'https://www.esign.cn/images/footerone.png',
  },
  {
    icon: 'https://www.esign.cn/images/weiboduck.png',
    url: 'https://www.esign.cn/images/footertwo.png',
  },
  {
    icon: 'https://www.esign.cn/images/zfbduck.png',
    url: 'https://www.esign.cn/images/footerthree.png',
  },
];
const qrRef = ref();
const triangleRef = ref();
const onMouseEnter = (index: number) => {
  if (qrRef.value[index] && triangleRef.value[index]) {
    qrRef.value[index].style.visibility = 'visible';
    triangleRef.value[index].style.visibility = 'visible';
  }
};
const onMouseLeave = (index: number) => {
  if (qrRef.value[index] && triangleRef.value[index]) {
    qrRef.value[index].style.visibility = 'hidden';
    triangleRef.value[index].style.visibility = 'hidden';
  }
};
</script>

<template>
  <div class="footer-container">
    <div class="footer-container-our">
      <div class="footer-container-our-left">
        <div
          class="footer-container-our-left-item"
          v-for="(item, index) in footItem"
          :key="index"
        >
          <div class="footer-container-our-left-title">{{ item.title }}</div>
          <div
            class="footer-container-our-left-sub"
            v-for="(subItem, index) in item.sub"
            :key="index"
          >
            {{ subItem }}
          </div>
        </div>
      </div>
      <div class="footer-container-our-right">
        <div class="footer-container-our-right-title">服务热线</div>
        <div style="display: flex; flex-wrap: wrap">
          <div
            class="footer-container-our-right-item"
            v-for="(item, index) in serveList"
            :key="index"
          >
            <div class="footer-container-our-right-item-tel">
              {{ item.tel }}
            </div>
            <div class="footer-container-our-right-item-name">
              {{ item.name }}
            </div>
          </div>
        </div>
        <div style="display: flex">
          <div
            class="icon-container"
            v-for="(item, index) in iconArr"
            :key="index"
          >
            <div
              class="icon-container-item"
              style="height: 30px; width: 30px"
              @mouseenter="onMouseEnter(index)"
              @mouseleave="onMouseLeave(index)"
            >
              <img :src="item.icon" height="30px" width="30px" />
            </div>
            <div class="icon-container-qr" ref="qrRef">
              <img :src="item.url" height="100px" width="100px" />
            </div>
            <div ref="triangleRef" class="triangle"></div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-container-bottom">
      <div>
        <span style="padding-right: 5px">友情链接:</span>
        <span class="link-item" v-for="(item, index) in linkList" :key="index">
          {{ item }}
        </span>
      </div>
      <div style="margin: 10px">
        <span class="copy-right">
          Copyright © 2021
          杭州天谷信息科技有限公司版权所有.增值电信业务经营许可证浙B2-20180376号浙ICP备11026113号-4浙公网安备33010602010810号
        </span>
      </div>
      <div>
        <span
          class="agreement-item"
          v-for="(item, index) in agreementLinkList"
          :key="index"
        >
          {{ item }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.footer-container {
  width: 100%;
  height: 540px;
  .footer-container-our {
    width: 100%;
    height: 400px;
    box-sizing: border-box;
    background: #242424;
    padding: 50px 10px;
    display: flex;
    .footer-container-our-left {
      flex: 3;
      display: flex;
      justify-content: right;
      .footer-container-our-left-item {
        margin-right: 10%;
        .footer-container-our-left-title {
          color: white;
          text-align: left;
          margin-bottom: 20px;
        }
        .footer-container-our-left-sub {
          color: #999999;
          line-height: 30px;
        }
        .footer-container-our-left-sub:hover {
          color: red;
          cursor: pointer;
        }
      }
    }
    .footer-container-our-right {
      flex: 2;
      display: flex;
      flex-direction: column;
      .footer-container-our-right-title {
        color: white;
        text-align: left;
        margin-bottom: 20px;
      }
      .footer-container-our-right-item {
        width: 40%;
        margin-right: 10px;
        margin-bottom: 10px;
        .footer-container-our-right-item-tel {
          font-size: 16px;
          font-weight: 600;
          color: #fff;
          line-height: 22px;
        }
        .footer-container-our-right-item-tel:hover {
          color: red;
          cursor: pointer;
        }
        .footer-container-our-right-item-name {
          margin-top: 4px;
          line-height: 20px;
          color: #999999;
        }
      }
      .icon-container {
        height: 50px;
        display: flex;
        margin-top: 30px;
        position: relative;
        .icon-container-item {
          margin-right: 50px;
          border-radius: 50px;
        }
        .icon-container-item:hover {
          img {
            filter: brightness(200%); /* 将图像变得更加明亮，达到白色的效果 */
          }
        }
        .icon-container-qr {
          position: absolute;
          height: 100px;
          width: 100px;
          left: 0;
          top: 50px;
          visibility: hidden;
        }
        .triangle {
          position: absolute;
          width: 0;
          height: 0;
          border-left: 8px solid transparent; /* 左边框宽度为0，高度为0 */
          border-right: 8px solid transparent; /* 右边框宽度为0，高度为0 */
          border-bottom: 8px solid white; /* 底部边框宽度为10px，高度为10px，颜色为红色 */
          top: 42px;
          left: 8px;
          visibility: hidden;
        }
      }
    }
  }
  .footer-container-bottom {
    min-height: 140px;
    width: 100%;
    text-align: center;
    color: #999;
    line-height: 17px;
    font-size: 12px;
    background: #333;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .link-item {
      display: inline-block;
    }
    .link-item:hover {
      color: white;
      cursor: pointer;
    }
    .link-item:not(:last-child)::after {
      content: '|';
      color: #999999;
      padding-left: 4px;
      padding-right: 4px;
    }
    .agreement-item {
      display: inline-block;
    }
    .agreement-item:not(:last-child)::after {
      content: '|';
      padding: 0 4px;
    }
  }
}
</style>
