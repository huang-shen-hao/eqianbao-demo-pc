<script setup lang="ts">
// 左侧点击事件
import { onMounted, ref } from 'vue';
// 记录当前点击的index
let currentIndex = ref<number>(0);
const onDivClick = (index: number) => {
  currentIndex.value = index;
  const mainLeftItem = document.querySelectorAll('.main-left-item');
  if (mainLeftItem[index]) {
    //动态添加active类 实现高度变化
    mainLeftItem[index]?.classList.add('active');
    // 设置对应背景
    const arr = mainLeftItem[index].classList.value;
    // console.log('ooo', arr);
    if (arr && arr.includes('active')) {
      mainLeftItem[index].style.background =
        `url(${leftList[index].image}) center center no-repeat`;
      mainLeftItem[index].style.backgroundSize = 'cover';
    }
    // 排他操作
    const arr4 = [0, 1, 2, 3, 4, 5].filter((item) => item != index);
    console.log('ooo', arr4);
    arr4.forEach((item) => {
      if (mainLeftItem[item]) {
        mainLeftItem[item]?.classList.remove('active');
        mainLeftItem[item].style.background = '#f6f6f9';
      }
    });
  }
};
onMounted(() => {
  onDivClick(0);
});
const leftList = [
  {
    title: '公有云',
    remark: '成长型企业',
    content:
      '提供签管一体化的电子合同云服务，可通过SaaS进行合同签署与管理，也可通过API无缝集成到业务系统中。',
    image:
      'https://trial-cdn.esign.cn/upload/18f98a20-08ef-5bf6-b996-9ab240fc38a7!!5-7.png',
  },
  {
    title: '混合云',
    remark: '集团型企业',
    content:
      '核心资源不出本地，为中大型企业打造专属定制系统，提供多应用场景下合同管理、电子签章、实体印章、用印管理的一体化解决方案。',
    image:
      'https://trial-cdn.esign.cn/upload/c457c616-f05b-5baf-867f-e91e21904fc1!!5-7.png',
  },
  {
    title: '行业云',
    remark: '公共事业',
    content:
      '提供丰富便捷的行业化电子签名场景解决方案，促进政府、医院、学校等公共服务事业单位实现全面数字化转型。',
    image:
      'https://trial-cdn.esign.cn/upload/78fcac06-4d15-5daf-bfa8-43e8b796d3f3!!5-7.png',
  },
  {
    title: '超阅',
    remark: 'OFD办公',
    content:
      '高效、好用的中国标准OFD版式文档办公产品，通过互联网+人工智能为每个组织、个人提供数字办公。',
    image:
      'https://trial-cdn.esign.cn/upload/e35adf46-412b-5e35-b648-01dce47a36aa!!5-7.png',
  },
  {
    title: '法律服务',
    remark: 'OFD办公',
    content:
      '联合权威机构，为用户打造安全无忧的法律保障服务体系；结合业务场景，为用户定制合理有效的电子签约合规方案。',
    image:
      'https://trial-cdn.esign.cn/upload/3568d92d-2a90-5caa-b5da-ae104ab98375!!5-7.png',
  },
];
const rightList = [
  [
    {
      title: '电子签名API',
      content: '提供丰富的API接口与页面嵌入，让业务系统快速集成电子签能力',
      tag: ['SaaS API', '基础能力API', '开放平台'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: '电子合同SaaS',
      content: '服务成长型企业管人事、做生意的在线合同签管一体化平台',
      tag: ['基础版', '专业版', '高级版', '智能版'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: 'e签盾',
      content: 'CA数字证书管理与行业应用的整体解决方案',
      tag: ['身份认证', '电子签章', '加密解密'],
      button: ['免费试用', '在线咨询'],
    },
  ],
  [
    {
      title: '天印',
      content: '企业级集团化电子签章一体化平台',
      tag: ['文档中心', '签署中心', '印控中心', '证据中心'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: '信创签章',
      content: '国内领先的信创电子签章套件',
      tag: ['国密/商密印章管理', 'PDF签署', 'OFD签署', '密钥管理'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: '铁证证据管理系统',
      content: '企业级私有化区块链业务存证平台',
      tag: ['证据管理', '自定义证据链', '自定义报告', '在线出证'],
      button: ['免费试用', '在线咨询'],
    },
  ],
  [
    {
      title: '统一电子印章平台',
      content:
        '建设一体化电子印章公共服务基础设施平台，助力全社会实现数字化转型',
      tag: ['印章申领', '签署管理', '应用中心', '统一监管'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: '电子场景应用平台',
      content:
        '提供丰富多样化的场景应用解决方案，普及电子印章应用，支撑政务服务标准化、规范化、便利化',
      tag: ['入职管理', '员工花名册', '合同签署', '合同签署'],
      button: ['免费试用', '在线咨询'],
    },
    {
      title: '医签宝',
      content: '做最懂医疗的电子签名产品',
      tag: ['医护签名', '患者签名', '手写板签名', '电子病例签名'],
      button: ['免费试用', '在线咨询'],
    },
  ],
  [
    {
      title: '超阅',
      content: '好用的中国标准OFD版式文档办公产品',
      tag: ['办公套件', '处理器', '设计器', '超阅云'],
      button: ['免费试用', '在线咨询'],
    },
  ],
  [
    {
      title: '法律合规',
      content:
        '联合权威机构，打造安全无忧的法律保障服务体系；结合业务场景，定制合法有效的电子签约合规方案',
      tag: ['证据报告', '司法鉴定', '流程公证', '法律服务'],
      button: ['免费试用', '在线咨询'],
    },
  ],
];
const rightImgList = [
  'https://trial-cdn.esign.cn/upload/25e66a3c-ddb5-596d-9b2d-0d6404568fd7!!5-12.png',
  'https://trial-cdn.esign.cn/upload/9830cae2-8ddf-50f6-a966-c5655d58abd1!!5-12.png',
  'https://trial-cdn.esign.cn/upload/fbea8c5a-0683-52b6-8aac-db06843f312f!!5-12.png',
  'https://trial-cdn.esign.cn/upload/8adcaa97-2b4b-5cb4-8c53-80eb77121dae!!5-12.png',
  'https://trial-cdn.esign.cn/upload/022869de-c4a1-55c4-8c02-87581cb303cf!!5-12.png',
];
</script>

<template>
  <div class="container">
    <p class="p1">丰富、安全、稳定的产品服务</p>
    <div class="main">
      <!--左边-->
      <div class="main-left">
        <div
          class="main-left-item"
          :class="{ active: index === 0 }"
          v-for="(item, index) in leftList"
          :key="index"
          @click="onDivClick(index)"
        >
          <div>
            <span class="span1">{{ item.title }}</span>
            <span class="span2">({{ item.remark }})</span>
            <span class="span3">{{ item.content }}</span>
          </div>
        </div>
      </div>
      <div class="main-right">
        <div
          class="main-right-item"
          v-for="(item, index) in rightList[currentIndex]"
          :key="index"
        >
          <!--标题-->
          <p class="right-title">{{ item.title }}</p>
          <!--内容-->
          <p class="right-content">{{ item.content }}</p>
          <!--标签-->
          <div class="tag-container">
            <span v-for="tagItem in item.tag" :key="tagItem">
              {{ tagItem }}
            </span>
          </div>
          <!--按钮-->
          <div>
            <span
              class="btn-container"
              v-for="buttonItem in item.button"
              :key="buttonItem"
            >
              {{ buttonItem }}
            </span>
          </div>
        </div>
        <!--图片-->
        <div class="img-container">
          <!--图片在右下角的样式-->
          <img
            v-if="
              currentIndex === 0 || currentIndex === 1 || currentIndex === 2
            "
            class="img1"
            :src="rightImgList[currentIndex]"
          />
          <!--图片在底部的样式-->
          <img
            v-if="currentIndex === 3 || currentIndex === 4"
            class="img2"
            :src="rightImgList[currentIndex]"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  height: 900px;
  background: url(https://trial-cdn.esign.cn/upload/8a99deb0-42c5-5db7-ad4d-17af48ec5bec!!5-20.jpg)
    50% / cover no-repeat;
  z-index: 0;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .p1 {
    font-size: 32px;
    line-height: 50px;
    color: rgba(0, 0, 0, 0.85);
    font-weight: 600;
    text-align: center;
    padding: 40px 0 0 0;
  }
  .main {
    width: 85%;
    display: flex;
    .main-left {
      width: 40%;
      height: 100%;
      .main-left-item {
        width: 100%;
        height: 120px;
        border-bottom: 1px solid #f5f1f1;
        box-sizing: border-box;
        padding: 20px;
        box-shadow: 0 4px 10px 0 hsla(0, 0%, 83.5%, 0.5);
        text-align: left;
        cursor: pointer;
        .span1 {
          font-size: 20px;
          font-weight: 600;
          color: #000000;
        }
        .span2 {
          font-size: 14px;
          font-weight: 600;
          color: #000000;
          padding-left: 4px;
        }
        .span3 {
          font-size: 14px;
          font-weight: 400;
          color: rgba(0, 0, 0, 0.65);
          line-height: 20px;
          text-shadow: 0 4px 10px hsla(0, 0%, 83.5%, 0.5);
          display: inline-block;
          white-space: nowrap; //不允许换行
          width: 100%;
          overflow: hidden;
          text-overflow: ellipsis;
          padding-top: 20px;
        }
      }
      .main-left-item.active {
        height: 240px;
        .span1 {
          color: red;
        }
        .span2 {
          color: red;
        }
        .span3 {
          white-space: normal; //忽略多余的空白字符，合并连续的空白字符，并在必要时进行换行。
        }
      }
    }
    .main-right {
      width: 60%;
      box-sizing: border-box;
      position: relative; //产生层叠上下文
      background-color: white;
      .main-right-item {
        position: relative;
        width: 100%;
        height: 240px;
        box-sizing: border-box;
        padding: 20px 66px;
        border-bottom: 1px solid #f5f1f1;
        z-index: 1;
        .right-title {
          font-size: 20px;
          color: rgba(0, 0, 0, 0.85);
          line-height: 28px;
          font-weight: 600;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
        }
        .right-content {
          font-size: 14px;
          font-weight: 400;
          color: rgba(0, 0, 0, 0.65);
          line-height: 20px;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          margin-top: -10px;
        }
        .tag-container {
          span {
            display: inline-block;
            min-width: 66px;
            height: 18px;
            line-height: 18px;
            border-radius: 4px;
            border: 1px solid rgba(0, 0, 0, 0.65);
            margin-right: 11px;
            text-align: center;
            padding: 0 7px;
            font-size: 14px;
            color: rgba(0, 0, 0, 0.65);
          }
        }
        .btn-container {
          display: inline-block;
          border: 1px solid red;
          width: 100px;
          height: 30px;
          margin-right: 20px;
          margin-top: 20px;
          text-align: center;
          line-height: 30px;
          cursor: pointer;
          color: #999999;
        }
        .btn-container:first-child {
          transition: background-color 0.3s ease; /* 添加过渡效果 */
        }
        .btn-container:first-child:hover {
          background-color: #cc0000;
          color: white;
        }
      }
      .img1 {
        position: absolute;
        width: 480px;
        height: 500px;
        bottom: 0;
        right: 0;
        z-index: 0;
      }
      .img2 {
        position: absolute;
        width: 100%;
        height: 300px;
        bottom: 0;
        right: 0;
        z-index: 0;
      }
    }
  }
}
</style>
