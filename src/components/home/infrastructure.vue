<script setup lang="ts">
import { ref } from 'vue';
const mainList = [
  {
    name: '系统安全',
    arr: ['·cmmi3认证', '·可信云认证', '·ISO认证'],
    content:
      '所有硬件均经过国家相关安全机构检测，实现信创全产业链适配，所有软件均按照银行安全级别进行设计开发，具有与纸质签署同等法律效力',
    icon: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/xtaq-icon.b15b72e.png',
    img: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/xtaq-bg.0327723.png',
  },
  {
    name: '数据安全',
    content:
      '以权威数字签名为基础，采用安全加密技术，确保组织的签署数据自动记录，防伪、防篡改',
    arr: ['·数据采集·数据存储', '·数据共享·数据传输', '·数据使用·数据销毁'],
    icon: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/sjaq-icon.3bde2f2.png',
    img: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/sjaq-bg.16cf677.png',
  },
  {
    name: '应用安全',
    content:
      'e签宝在产品安全性保障上主要参考行业最佳实践：微软的SDL模型（即软件安全开发周期）',
    arr: ['·需求设计', '·编码测试', '·应用发布', '·产品运营'],
    icon: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/yyaq-icon.aaeb3ce.png',
    img: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/yyaq-bg.f2b7394.png',
  },
  {
    name: '管理合规',
    content:
      'e签宝制定且严格执行《信息安全守则》《隐私事件处理规范》等一系列安全合规管理制度，并由行业领先的安全专家团队建立应急响应、安全攻防、安全开发等合规管理组织',
    arr: ['·人员管理', '·设备管理', '·流程合规', '·应急响应'],
    icon: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/glhg-icon.da74ef9.png',
    img: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/glhg-bg.3edc40b.png',
  },
  {
    name: '法律保障',
    content: '产品设计符合《电子签名法》规定，全流程签署合法有效',
    arr: ['·电子签名法', '·电子认证业务规则', '·个人信息保护法'],
    icon: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/flbz-icon.35df45f.png',
    img: 'https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/flbz-bg.99e11d5.png',
  },
];
const mainItemRef = ref();
const detailContainerRef = ref();
const showPha = ref<boolean>(false); //段落
const iconRef = ref(); //右小角图标
let currentIndex = ref<number>(0); //记录当前对象 显示隐藏icon之类
const mouseEnter = (index: number) => {
  currentIndex.value = index;
  if (mainItemRef.value[index]) {
    mainItemRef.value[index].style.width = '32%';
    mainItemRef.value[index].style.background = `url(${mainList[index].img})`; //替换背景图片
    mainItemRef.value[index].style.backgroundPosition = 'center center';
    mainItemRef.value[index].style.backgroundSize = 'cover';
  }
  if (detailContainerRef.value) {
    detailContainerRef.value[index].style.visibility = 'hidden';
  }
  if (iconRef.value) {
    iconRef.value[index].style.visibility = 'hidden';
  }
  showPha.value = true;
  // 改变其他的宽度
  const arr = [0, 1, 2, 3, 4].filter((item) => item !== index);
  arr.forEach((item) => {
    if (mainItemRef.value[item]) {
      mainItemRef.value[item].style.width = '17%';
    }
  });
};
const mouseLeave = () => {
  showPha.value = false;
  if (mainItemRef.value) {
    mainItemRef.value.forEach((item: any) => {
      item.style.width = '25%';
      item.style.background = 'white';
    });
  }
  if (detailContainerRef.value[currentIndex.value]) {
    detailContainerRef.value[currentIndex.value].style.visibility = 'visible';
  }
  if (iconRef.value[currentIndex.value]) {
    iconRef.value[currentIndex.value].style.visibility = 'visible';
  }
};
</script>

<template>
  <div class="infrastructure-container">
    <p class="infrastructure-container-title">安全合规的基础设施</p>
    <div class="infrastructure-container-main">
      <div
        class="infrastructure-container-main-item"
        v-for="(item, index) in mainList"
        :key="index"
        @mouseenter="mouseEnter(index)"
        @mouseleave="mouseLeave"
        ref="mainItemRef"
      >
        <p class="infrastructure-container-main-item-title">{{ item.name }}</p>
        <div ref="detailContainerRef">
          <!--小标题-->
          <span
            class="infrastructure-container-main-item-detail"
            v-for="j in item.arr"
            :key="j"
          >
            {{ j }}
          </span>
        </div>
        <div v-show="showPha && index === currentIndex">
          <!--段落-->
          <span class="infrastructure-container-main-item-pha">
            {{ item.content }}
          </span>
        </div>
        <div>
          <i
            ref="iconRef"
            class="icon"
            :style="{
              backgroundImage: `url(${item.icon})`,
            }"
          ></i>
        </div>
      </div>
    </div>
    <div class="infrastructure-container-people">
      <div class="infrastructure-container-people-left">
        <p class="infrastructure-container-people-left-title">
          大咖说·安全合规
        </p>
        <div class="infrastructure-container-people-left-detail">
          <span>
            e签宝采用基于pki体系的非对称加密算法，结合摘要散列计算技术，能够确保每一份文件签署过程的真实可靠。签署时验证签名人本人的真实意愿，符合《中华人民共和国电子签名法》对于“可靠电子签名”的法规要求，同时满足《GB/T
            38540 安全电子签章密码技术规范》的要求。
          </span>
        </div>
      </div>
      <div class="infrastructure-container-people-right">
        <div class="name"><span>吕述望</span></div>
        <div class="introduce">
          <span style="display: block">北京知识安全工程中心主任</span>
          <span style="display: block">中国科学院信工所DCS中心创建人</span>

          <span style="display: block">
            信息安全国家重点实验室教授，博士生导师
          </span>
        </div>
      </div>
    </div>
    <div style="margin: 30px 0">
      <div style="cursor: pointer">
        <a href="https://www.esign.cn/pcgw/cp/aqhg/" style="color: #cc0000">
          了解更多>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
a {
  text-decoration: none; //去除下划线
}
.infrastructure-container {
  width: 100%;
  height: 744px;
  background: url('https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/aqhg-bg.3f240be.jpg')
    no-repeat center center;
  background-size: contain;
  display: flex;
  align-items: center;
  flex-direction: column;
  .infrastructure-container-title {
    padding-bottom: 46px;
    font-size: 32px;
    font-weight: 600;
    color: rgba(0, 0, 0, 0.85);
    line-height: 50px;
    text-align: center;
  }
  .infrastructure-container-main {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 90%;
    height: 210px;
    .infrastructure-container-main-item {
      position: relative;
      height: 100%;
      box-sizing: border-box;
      width: 20%;
      background-color: white;
      margin-right: 2px;
      transition: width 0.5s ease-in-out;
      .infrastructure-container-main-item-title {
        font-size: 18px;
        font-weight: 600;
        color: rgba(0, 0, 0, 0.85);
        line-height: 25px;
        margin-left: 18px;
      }
      .infrastructure-container-main-item-detail {
        font-size: 14px;
        box-sizing: border-box;
        padding: 4px 0;
        display: block;
        color: #999999;
        margin-left: 18px;
      }
      .icon {
        position: absolute;
        right: 5%;
        bottom: 20px;
        display: inline-block;
        width: 46px;
        height: 46px;
        background-size: contain;
        background-position: center center;
        background-repeat: no-repeat;
      }
      .infrastructure-container-main-item-pha {
        position: absolute;
        top: 30%;
        left: 20px;
        max-width: 246px;
        width: 100%;
        font-size: 14px;
        font-weight: 400;
        color: rgba(0, 0, 0, 0.65);
        line-height: 20px;
      }
    }
  }
  .infrastructure-container-people {
    width: 90%;
    height: 210px;
    background: url('https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/lsw-teacher-bg.6a03b0b.jpg')
      no-repeat center center;
    background-size: cover;
    margin-top: 20px;
    box-shadow: 2px 2px 12px 0 rgba(219, 229, 238, 0.8);
    display: flex;
    .infrastructure-container-people-left {
      .infrastructure-container-people-left-title {
        font-size: 20px;
        font-weight: 600;
        margin-left: 2%;
      }
      .infrastructure-container-people-left-detail {
        max-width: 70%;
        color: #000000;
        font-size: 14px;
        margin-left: 2%;
        line-height: 24px;
      }
    }
    .infrastructure-container-people-right {
      position: relative;
      box-sizing: border-box;
      height: 100%;
      font-size: 14px;
      font-weight: 400;
      color: hsla(0, 0, 100%, 0.85);
      padding: 0 480px 0 0;
      line-height: 20px;
      background: url(//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/lsw-teacher.099e3a3.png)
        0 / cover no-repeat;
      .name {
        position: absolute;
        top: 35%;
        left: 50%;
      }
      .introduce {
        position: absolute;
        top: 50%;
        left: 50%;
        max-width: 220px;
      }
    }
  }
}
</style>
