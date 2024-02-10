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
        <div class="main-right-item">右边</div>
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
    height: 660px;
    display: flex;
    .main-left {
      width: 40%;
      height: 100%;
      .main-left-item {
        width: 100%;
        height: 120px;
        border-bottom: 2px solid black;
        box-sizing: border-box;
        padding: 20px;
        box-shadow: 0 4px 10px 0 hsla(0, 0%, 83.5%, 0.5);
        text-align: left;
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
        height: 180px;
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
      height: 660px;
      background-color: #333333;
    }
  }
}
</style>
