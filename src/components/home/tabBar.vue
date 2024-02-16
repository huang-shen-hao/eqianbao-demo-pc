<script setup lang="ts">
// 顶部菜单名称

import { ref } from 'vue';

// 顶部右侧菜单
const topMenu = [
  {
    name: '查看价格',
    href: 'https://www.esign.cn/site/quotation',
  },
  {
    name: '登录',
    href: 'https://h5.esign.cn/usercenterFront/login',
  },
  {
    name: '注册',
    href: 'https://h5.esign.cn/usercenterFront/regist?pub=esign',
  },
];
const jump = (address: string) => {
  window.location.href = address; //跳转
};
// 几个二维码
const qrType = [
  {
    type: '微信端',
    title: '使用微信扫一扫',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2020/09/10/29066.png?1651743977350',
    icon: 'iconfont icon-weixin-copy',
  },
  {
    type: '支付宝',
    title: '使用支付宝扫一扫',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2020/09/10/29072.png?1651743977354',
    icon: 'iconfont icon-zhifubao',
  },
  {
    type: 'IOS版本',
    title: '扫一扫下载IOS客户端',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2021/12/27/32251.png?1651743977358',
    icon: 'iconfont icon-ios',
  },
  {
    type: '安卓版',
    title: '扫一扫下载安卓客户端',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2022/04/28/32543.png?1651743977362',
    icon: 'iconfont icon-anzhuo',
  },
  {
    type: '钉钉端',
    title: '使用钉钉扫一扫',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2020/09/10/29075.png?1651743977366',
    icon: 'iconfont icon-dingding',
  },
  {
    type: '客户端',
    title: '点击打开客户端下载页',
    picUrl:
      'https://www.esign.cn/upload/resources/image/2021/09/24/31942.png?1651743977369',
    icon: 'iconfont icon-client2',
  },
];

const qrItems = ref<HTMLElement[] | null>(null);
// 第一个默认
const onHover = () => {
  if (qrItems.value) {
    console.log('ppppp', qrItems.value[0]);
    qrItems.value[0].style.backgroundColor = 'white';
    qrItems.value[0].style.borderLeft = '2px solid red';
    const icon = qrItems.value[0].querySelector('.QrCode_left_item_icon');
    const pic = qrItems.value[0].querySelector('.pic');
    if (icon) icon.style.backgroundColor = 'green';
    if (pic) pic.style.display = 'block';

    console.log('ppp', icon, pic);
  }
};
const changeBackground = (index: number) => {
  console.log('ppppp', index, qrItems.value);
  // 针对第一个默认选中 当其他选中时 去除第一个默认选中的样式
  if (index !== 0 && qrItems.value) {
    qrItems.value[0].style.backgroundColor = '#f3efef';
    qrItems.value[0].style.borderLeft = '2px solid #f3efef';
  }
  if (index === 0 && qrItems.value) {
    qrItems.value[0].style.backgroundColor = 'white';
    qrItems.value[0].style.borderLeft = '2px solid red';
  }
};
const resetBackground = () => {
  if (qrItems.value) qrItems.value[0].style.backgroundColor = ''; // 或者恢复默认的背景颜色
};
// 这几个是一个样式的
const list = [
  {
    name: '产品',
    content:
      'e签宝提供完整的全生态电子签名服务及产品，满足成长型企业、集团型企业、公共服务行业等客户的差异化需求，助力用户系统性解决签署难题，降本增效。',
    attr: [
      {
        title: '公有云产品',
        arr: ['签管一体化电子合同云平台', '钉钉智能合同'],
      },
      {
        title: '本地化产品',
        arr: ['企业统一印章平台', '政务统一印章平台'],
      },
      {
        title: '更多能力',
        arr: ['开放服务', '身份认证', '存证服务', '法律服务'],
      },
    ],
  },
  {
    name: '方案',
    content:
      '针对不同行业特点及业务场景，e签宝为客户深度定制个性化的电子签名解决方案，以满足实际应用需求，为用户带来真正便捷、高效、安全的使用体验。',
    attr: [
      {
        title: '行业解决方案',
        arr: [
          '在线教育',
          '银行/证券基金/保险',
          '医药制造/医疗卫生',
          '融资租赁',
          '不动产开发（地产）',
          '汽车',
          '物流',
          '快消行业',
          '制造业',
          '人力资源服务',
        ],
      },
      {
        title: '公共服务解决方案',
        arr: ['数字政府', '不动产行业'],
      },
      {
        title: '生态集成解决方案',
        arr: ['蓝凌数字化融合方案'],
      },
      {
        title: '创新业务',
        arr: ['海外签产品解决方案'],
      },
    ],
  },
  {
    name: '案例',
    content:
      '基于完整的安全合规体系，e签宝为客户提供专业可靠的全程服务保障，从免费体验、电子合同工具箱到在线客服，全面细致、快速响应。',
    attr: [
      {
        title: '客户案例',
        arr: ['客户案例', '客户证言'],
      },
    ],
  },
  {
    name: '服务',
    content:
      '基于完整的安全合规体系，e签宝为客户提供专业可靠的全程服务保障，从免费体验、电子合同工具箱到在线客服，全面细致、快速响应。',
    attr: [
      {
        title: '体验',
        arr: ['体验中心'],
      },
      {
        title: '工具',
        arr: ['合同验签', '合同模板'],
      },
      {
        title: '安全合规',
        arr: ['安全合规体系'],
      },
      {
        title: '客户服务',
        arr: ['服务中心', '帮助中心'],
      },
    ],
  },
  {
    name: '行业资讯',
    content:
      '这里是行业风向标，可以查看关于电子签名的最新政策、行业资讯以及法律条文等，还有e签宝的最新企业动态、活动信息、签约资讯等。',
    attr: [
      {
        title: '资讯',
        arr: ['公司动态', '行业动态', '政策速递'],
      },
      {
        title: '智库',
        arr: ['行业报告', '法律智库', '知识科普'],
      },
    ],
  },
];
// 这几个是一个样式的
const list2 = [
  {
    name: '招募合作',
    leftTitle: '“e”起同行 共赢未来',
    leftContent:
      'e签宝坚持双赢思维，持续寻找优秀的生态伙伴强强联合，深度融合；另外还在全国范围内招募渠道合作伙伴，共享电子签名市场红利。',
    url: '//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/zmhz-bg.ecf6134.png',
    rightTitle: '招募合作',
    rightArr: ['生态合作', '个人合伙人'],
  },
  {
    name: '关于我们',
    leftTitle: '关于我们',
    leftContent:
      '从2002年出发，e签宝已专注电子签名行业19年，以 “让签署更便捷，让信任更简单”为自身使命，通过持续的投入与努力，以优质的产品与服务，不断引领行业向前。',
    url: '//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/about-bg.7309e33.png',
    rightTitle: '关于我们',
    rightArr: ['公司介绍', '荣誉资质', '加入我们', '联系我们'],
  },
];
// 展示list菜单对应的内容框
const showInfo = (index: number) => {
  console.log('index', index);
  const menuItem = document.querySelectorAll('.bottom_menu'); //拿前五个正好对应index
  if (menuItem[index]) {
    menuItem[index].style.color = 'red'; // 菜单字体变色
    // 找对应的info_container
    const infoContainer = menuItem[index].querySelector('.info_container');
    const infoContainer2 = menuItem[index].querySelector('.info_container_2'); //有两个且 不一样的背景
    // console.log(infoContainer,infoContainer2)
    if (infoContainer) infoContainer.style.visibility = 'visible'; //hover时候显示
    if (infoContainer2) infoContainer2.style.visibility = 'visible'; //hover时候显示
  }
  console.log('item', menuItem);
};
// 重置样式
const resetInfoStyle = (index: number) => {
  const menuItem = document.querySelectorAll('.bottom_menu'); //拿前五个正好对应index
  if (menuItem[index]) menuItem[index].style.color = 'black';
  // 找对应的info_container
  const infoContainer = menuItem[index].querySelector('.info_container');
  const infoContainer2 = menuItem[index].querySelector('.info_container_2');
  if (infoContainer) infoContainer.style.visibility = 'hidden'; //离开时时候隐藏
  if (infoContainer2) infoContainer2.style.visibility = 'hidden'; //离开时时候隐藏
};
</script>

<template>
  <div class="container">
    <div class="top">
      <!--左侧图片-->
      <div class="top_left">
        <a href="https://www.esign.cn/">
          <img src="@/assets/e签宝.png" alt="e签宝" />
        </a>
      </div>
      <!--右侧菜单-->
      <div class="top_right">
        <div class="top_right_item QrCode_show">
          <span @mouseover="onHover">客户端/小程序/APP</span>
          <div class="QrCode">
            <div class="QrCode_left">
              <!--左侧类型-->
              <div
                :class="{ QrCode_left_item: true, firstItem: index === 0 }"
                v-for="(item, index) in qrType"
                :key="item.type"
                @mouseover="changeBackground(index)"
                @mouseout="resetBackground"
                ref="qrItems"
              >
                <div class="QrCode_left_item_icon">
                  <i :class="item.icon" />
                </div>
                <div style="color: black">
                  {{ item.type }}
                </div>
                <!--右侧图片-->
                <div class="pic">
                  <div>
                    <img :src="item.picUrl" width="200" height="200" />
                  </div>
                  <div style="color: #999999">
                    {{ item.title }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="top_right_item" v-for="item in topMenu" :key="item.name">
          <span style="cursor: pointer" @click="jump(item.href)">
            {{ item.name }}
          </span>
        </div>
        <el-button class="top_button">免费试用</el-button>
      </div>
    </div>
    <div class="bottom">
      <div
        class="bottom_menu"
        v-for="(item, index) in list"
        :key="item.name"
        @mouseover="showInfo(index)"
        @mouseout="resetInfoStyle(index)"
      >
        <span>{{ item.name }}</span>
        <div class="info_container">
          <div class="info_container_left">
            <div class="info_container_left_title">
              {{ item.name }}
            </div>
            <p>
              {{ item.content }}
            </p>
          </div>
          <div class="info_container_right">
            <!-- 一个个竖着的列表-->
            <div
              style="margin: 10px 30px"
              v-for="e in item.attr"
              :key="e.title"
            >
              <div class="title">{{ e.title }}</div>
              <div
                v-for="(j, index) in e.arr"
                :key="index"
                style="height: 36px"
              >
                <span style="color: #333333; font-size: 14px">{{ j }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div
        class="bottom_menu"
        v-for="(item, index) in list2"
        :key="item.leftTitle"
        @mouseover="showInfo(index + 5)"
        @mouseout="resetInfoStyle(index + 5)"
      >
        <span>{{ item.name }}</span>
        <div class="info_container_2">
          <div
            class="info_container_2_left"
            :style="{
              backgroundImage: `url(${item.url})`,
              backgroundRepeat: 'no-repeat',
              backgroundPosition: 'right',
            }"
          >
            <div style="padding-left: 100px; padding-top: 50px">
              {{ item.leftTitle }}
            </div>
            <p style="padding-left: 100px">{{ item.leftContent }}</p>
          </div>
          <div class="info_container_2_right">
            <!-- 一个个竖着的列表-->
            <div style="margin: 100px 100px; text-align: left">
              <div class="title">{{ item.rightTitle }}</div>
              <div
                v-for="(e, index) in item.rightArr"
                :key="index"
                style="height: 36px"
              >
                <span style="color: #333333; font-size: 14px">{{ e }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div
        class="bottom_menu"
        @mouseover="showInfo(7)"
        @mouseout="resetInfoStyle(7)"
      >
        <span>开放平台</span>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  height: 111px;
  position: fixed;
  z-index: 10000;
  top: 0;
  background-color: white;
  .top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    .top_left {
      margin-left: 10px;
      img {
        width: 100px;
        height: 60px;
      }
    }
    .top_right {
      display: flex;
      justify-content: center;
      align-items: center;
      .top_right_item {
        margin: 0 10px;
        color: #333333;
        font-size: 14px;
      }
      //实现非第一个元素 字体变色
      .top_right_item:not(:nth-child(1)):hover {
        color: red;
      }
      .top_button {
        background-color: #cc0000;
        width: 90px;
        height: 40px;
        color: white;
        margin: 0 20px;
      }
    }
  }
  //实现展示二维码
  .QrCode_show {
    position: relative;
    .QrCode {
      width: 100px;
      height: 240px;
      padding-top: 10px;
      display: flex; //图片二维码和类型
      background-color: white;
      color: #fff;
      position: absolute;
      top: 100%;
      left: 0;
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.3s ease-in-out;
    }
  }
  .QrCode_show:hover .QrCode {
    opacity: 1;
    visibility: visible;
    z-index: 9;
  }
  //QrCode左侧样式
  .QrCode_left {
    background-color: #f3efef;
    .QrCode_left_item {
      position: relative;
      display: flex;
      justify-content: start;
      align-items: center;
      height: 40px;
      width: 100px;
      padding-left: 18px;
      //提前加边框解决 hover时候抖动问题
      border-left: 2px solid #f3efef;
      .QrCode_left_item_icon {
        width: 22px;
        height: 22px;
        border-radius: 50%;
        background-color: gray;
        margin: 0 4px;
        //icon居中
        text-align: center;
        line-height: 22px;
      }
      .pic {
        background-color: white;
        width: 240px;
        height: 230px;
        position: absolute;
        top: 0;
        left: 118px;
        display: none;
        text-align: center;
        padding-top: 10px;
      }
    }
  }
  //icon背景颜色 二维码 暴力
  .QrCode_left_item:nth-child(1):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: green;
    }
    .pic {
      display: block;
    }
  }
  .QrCode_left_item:nth-child(2):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: blue;
    }
    .pic {
      display: block;
      top: -40px;
    }
  }
  .QrCode_left_item:nth-child(3):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: black;
    }
    .pic {
      display: block;
      top: -80px;
    }
  }
  .QrCode_left_item:nth-child(4):hover {
    border-left: 2px solid black;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: green;
    }
    .pic {
      display: block;
      top: -80px;
    }
  }
  .QrCode_left_item:nth-child(4):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: green;
    }
    .pic {
      display: block;
      top: -120px;
    }
  }
  .QrCode_left_item:nth-child(5):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: orange;
    }
    .pic {
      display: block;
      top: -160px;
    }
  }
  .QrCode_left_item:nth-child(6):hover {
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon {
      background-color: #bc2edc;
    }
    .pic {
      display: block;
      top: -200px;
    }
  }

  .bottom {
    width: 100%;
    height: 51px;
    display: flex;
    text-align: center;
    line-height: 51px;
    position: relative;
    .bottom_menu {
      margin: 0 20px;
      font-size: 14px;
      z-index: 9; //防止遮挡
      .info_container {
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        //height:400px;
        visibility: hidden; //一开始隐藏 哪个hover 对应显示
        display: flex;
        .info_container_left {
          color: white;
          width: 30%;
          min-height: 400px;
          text-align: left;
          background: #eeeef2
            url(//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/menu-left-bg.3a01b50.png)
            no-repeat 100% 100%;
          .info_container_left_title {
            margin-bottom: 16px;
            padding-left: 75px;
            padding-top: 20px;
            font-size: 20px;
            color: rgba(0, 0, 0, 0.85);
            line-height: 28px;
          }
          p {
            font-size: 14px;
            color: #666;
            line-height: 20px;
            padding-left: 75px;
          }
        }
        .info_container_right {
          color: white;
          width: 70%;
          min-height: 400px;
          background-color: #fdfdfd;
          display: flex;
          flex-wrap: wrap;
          text-align: left;
          .title {
            min-width: 114px;
            padding-bottom: 11px;
            border-bottom: 1px solid #d7d7d7;
            font-size: 16px;
            font-weight: 500;
            line-height: 22px;
            color: #c00;
          }
        }
      }
      //样式不一致所以单独一个
      .info_container_2 {
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        height: 400px;
        visibility: hidden; //一开始隐藏 哪个hover 对应显示
        display: flex;
        .info_container_2_left {
          width: 50%;
          min-height: 400px;
          margin-bottom: 16px;
          font-size: 20px;
          color: rgba(0, 0, 0, 0.85);
          line-height: 28px;
          text-align: left;
          background-color: white;
          p {
            font-size: 14px;
            color: #666;
            line-height: 20px;
          }
        }
        .info_container_2_right {
          width: 50%;
          min-height: 400px;
          background: white;
          .title {
            width: 114px;
            padding-bottom: 11px;
            border-bottom: 1px solid #d7d7d7;
            font-size: 16px;
            font-weight: 500;
            line-height: 22px;
            color: #c00;
          }
        }
      }
    }
    .bottom_menu:hover {
      cursor: default; /* 默认情况下的指针样式 */
    }
    .bottom_menu:nth-child(8):hover {
      cursor: pointer; /* 手指*/
    }
  }
}
</style>
