<script setup lang="ts">
import { onMounted, ref } from 'vue';

const imgList = [
  'https://trial-cdn.esign.cn/upload/7e518cf8-d537-5a27-bb8b-48c4eb899fbc!!5-13.jpg', //证券
  'https://trial-cdn.esign.cn/upload/d2ed503a-df6a-5fdd-9856-602ef5283b68!!5-13.jpg', //保险
  'https://trial-cdn.esign.cn/upload/db61ac48-fe69-58b7-a059-a5c874799c73!!5-13.jpg', //不动产物业
  'https://trial-cdn.esign.cn/upload/1f7a19c4-dceb-5d94-bca1-7c5f4a21b8c5!!5-13.jpg', //不动产（地产）
  'https://trial-cdn.esign.cn/upload/d4e8c92a-5561-5a84-b470-afcfe69f3a83!!5-13.jpg', //汽车
  'https://trial-cdn.esign.cn/upload/c90657ae-2fb0-5a81-a8af-c13e47a83f72!!5-13.jpg', //物流
  'https://trial-cdn.esign.cn/upload/cb89b4b7-74ed-5e2f-b300-a9d63fbf7814!!5-13.jpg', //人力资源服务
  'https://trial-cdn.esign.cn/upload/ca6cbc0b-97e6-5870-b6a8-4fa5b527cdf4!!5-13.jpg', //医疗卫生
  'https://trial-cdn.esign.cn/upload/95f5eb2b-e9c7-5d1a-8089-ab2fdecf7b6c!!5-13.jpg', //连锁经营
  'https://trial-cdn.esign.cn/upload/ef916d0a-44db-51ad-bad0-082e1b92cb22!!5-13.jpg', //国央企
  'https://trial-cdn.esign.cn/upload/0b9df07a-ffe1-5b2a-adf9-8d39a8456f51!!5-13.jpg', //制造业
  'https://trial-cdn.esign.cn/upload/ba39a3d8-0d5a-55e7-a391-7df19d86f7b8!!5-13.jpg', //快消行业
];
// 左边箭头
const ArrowLeft =
  'https://trial-cdn.esign.cn/upload/8bd037b8-38fc-51b5-9418-f9bdac1bd479!!5-12.png';
// 右边箭头
const ArrowRight =
  'https://trial-cdn.esign.cn/upload/8bd037b8-38fc-51b5-9418-f9bdac1bd479!!5-12.png';
const btnList = [
  {
    name: '银行/证券基金',
    title: '银行、证券基金行业电子签名解决方案',
    detail:
      '随着银行的数字化转型，纸质合同成为制约银行业务线上化的最后一环，针对银行业特点，对于用户数据隐私保密、行业强监管性、国产化适配等要求，e签宝提供专业的解决方案，助力银行迈入智能电子合同时代。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/deb03815-5914-5368-9bec-17bf2b6ed94e!!5-16.png',
  },
  {
    name: '保险',
    title: '保险行业电子签名解决方案',
    detail:
      '随着银保监会发布保险行业标准通知，明确定义了电子签章、电子认证服务、数字证书、加密算法等内容。其中，为保证保险电子单据具有与纸质单据相同的法律效力，应在保险电子单据的生成和使用等过程中应用可靠的电子签名技术。e签宝针对保险业的电子保函、电子投保单等场景提供专业的解决方案。',
    showBtn: false,
    demo: 'https://trial-cdn.esign.cn/upload/ea229e77-870f-556b-84ed-a775827532dd!!5-16.png',
  },
  {
    name: '不动产(物业)',
    title: '物业电子签名解决方案',
    detail:
      '物业企业降本增效、智能管理已成为保盘发展的最优路径。内部管理系统广泛覆盖，而纸质签字盖章却成为信息化断点，造成管理成本增加，徒增法律风险。引入e签宝电子签，链接业务，建立企业信息化通路，降成本、提效率、优化服务。',
    showBtn: false,
    demo: 'https://trial-cdn.esign.cn/upload/04359f75-2797-599b-9eb9-62da033e12c5!!5-16.png',
  },
  {
    name: '不动产开发(地产)',
    title: '地产行业电子签名解决方案',
    detail:
      '随着行业进入成熟期，逐渐形成集聚效应，强者恒强，而市场的成熟期也意味着进入了一定的瓶颈期，如何通过信息化手段达到降本增效，是很多房地产公司需要考虑的问题，而电子合同是重要的方式之一。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/519235ae-4783-53de-b0cc-60811d525159!!5-16.png',
  },
  {
    name: '汽车',
    title: '汽车行业电子签名解决方案',
    detail:
      '互联网在改变各行各业，出现了越来越多的互联网汽车服务平台，围绕着汽车后市场提供的服务内容，服务过程中迫切需要通过线上签订合同， 实现全流程不见面的网上交易。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/7b3c9ecc-6ba0-55d2-9e5e-4119568261c3!!5-16.png',
  },
  {
    name: '物流',
    title: '物流行业电子签名解决方案',
    detail:
      '随着物流行业信息化的整体深化，无纸化已成为物流转型升级的关键点，如何在可信、高效、安全、环保的行业背景下，追求速度的飞跃是物流行业在转型期普遍面对的难题，而电子签名时代的到来则给传统的物流模式带来了新变化。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/0a06bc7c-2486-5429-8c84-c510a70768c0!!5-16.png',
  },
  {
    name: '人力资源服务',
    title: '人力资源行业电子签名解决方案',
    detail:
      '企业在提供人力资源服务过程中，产生大量合同签署的需求，越来越多的企业开始引入更高效的签约方式，提升业务开展效率、降低业务开展成本，并解决服务过程中合约缔造的问题。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/9bed15ab-f60d-57e5-bf99-4a8f1433d643!!5-16.png',
  },
  {
    name: '医疗卫生',
    title: '医疗卫生行业电子签名解决方案',
    detail:
      '近年来医疗行业多项政策和标准都有明确提出在医疗行业建设需应用电子签名的要求，医疗信息化需要提供更加可信赖互认的基础能力，e签宝旗下“医签宝”产品正是将这些基础能力输入到智慧医疗卫生各领域，为医疗卫生行业用户打造IT信任底座，赋能智慧医疗体系建设。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/2b1a029f-14b2-5bd0-90bb-50c2bfff7bef!!5-16.png',
  },
  {
    name: '连锁经营',
    title: '连锁经营行业电子签名解决方案',
    detail:
      '连锁经营是在总部的管理下，进行专业化分工，并在分工基础上实施集中化管理，把独立的经营活动组合成整体的规模经营，实现规模效益。e签宝针对经销代理/连锁加盟协议、采购合同、物流出库入库单等场景提供专业的解决方案。',
    showBtn: false,
    demo: 'https://trial-cdn.esign.cn/upload/bfb205eb-bc87-55ff-be19-896c1f48d620!!5-16.png',
  },
  {
    name: '国央企',
    title: '国央企电子签名解决方案',
    detail:
      '随着国资委印发的《关于加快推进国有企业数字化转型工作的通知》明确指出推进产品创新数字化、推进生产运营智能化等内容，e签宝为助力国企数字化转型，提供国产化适配，合同数据隐私保护，企业集团化印章管控等服务。',
    showBtn: false,
    demo: 'https://trial-cdn.esign.cn/upload/afd1ba6c-c305-5c8c-9f99-926e9ee8e0dc!!5-16.png',
  },
  {
    name: '制造业',
    title: '制造业电子签名解决方案',
    detail:
      '制造业公司已经形成了一定规模，大都是集团型公司，通常有众多分支机构且分布广泛，这类企业由于业务需求会面临向各分支机构授权制定和使用印章，并且所涉及到的场景非常多，如何从原有线下模式转型线上化的方式，e签宝提供了成熟的解决方案。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/b4e37a95-8273-55c8-b4c2-7e62f8b1c358!!5-16.png',
  },

  {
    name: '快消行业',
    title: '快消行业电子签名解决方案',
    detail:
      '消费品市场需求量大、产品消耗快、需求重复、单品价格低、企业门槛低，行业竞争很是激烈，快消品产品的销售主要依靠线下门店和分销渠道，此外通过网络平台的销售。e签宝提供针对快消品供应链业务的电子签名应用帮助企业实现销售业务全过程的物流、资金流、信息流的有效管理和控制。',
    showBtn: true,
    demo: 'https://trial-cdn.esign.cn/upload/d05af2cc-1f82-5eb9-9825-03f81ab4f5b4!!5-16.png',
  },
];
// 按钮点击事件
// 当前index
let currentIndex = ref<number>(0);
// 轮播图实例
const planRef = ref();
const onBtnClick = (index: number) => {
  currentIndex.value = index;
  // 踩坑 命名重复 querySelectorAll拿到整个项目中类名一样的元素
  // const btn = document.querySelectorAll('.plan-container .main .btn-container');
  // console.log('lll', btn);
  planRef.value && planRef.value.setActiveItem(index);
};
// 滑动行为
// 找到包裹内容的div
const scrollWrapper = ref();
const containerRef = ref();
const startPosition = ref<number>(0); //获取鼠标初始位置
const isDragging = ref<boolean>(false); //是否在拖动
const handleMouseDown = (e: MouseEvent) => {
  startPosition.value = e.clientX;
  isDragging.value = true;
  e.preventDefault();
  containerRef.value?.addEventListener('mousemove', handleMouseMove);
  containerRef.value?.addEventListener('mouseup', handleMouseUp);
};
const handleMouseMove = (e: MouseEvent) => {
  if (isDragging.value) {
    e.preventDefault();
    const distance = e.clientX - startPosition.value;
    console.log('cc', distance);
    scrollWrapper.value.scrollLeft -= distance;
    startPosition.value = e.clientX;
  }
};

const handleMouseUp = (e: MouseEvent) => {
  e.preventDefault();
  isDragging.value = false;
  containerRef.value?.removeEventListener('mousemove', handleMouseMove);
  containerRef.value?.removeEventListener('mouseup', handleMouseUp);
};

onMounted(() => {
  scrollWrapper.value?.addEventListener('mousedown', handleMouseDown);
});

// onMounted(() => {
//   scrollWrapper.value?.addEventListener('mousedown', (e: MouseEvent) => {
//     isDragging.value = true;
//     e.preventDefault(); // 防止默认的文字选择行为
//   });
//   scrollWrapper.value?.addEventListener('mousemove', (e: MouseEvent) => {
//     if (isDragging.value) {
//       e.preventDefault(); // 防止默认的选择行为
//       const distance = e.clientX - startPosition.value;
//       scrollWrapper.value.scrollLeft -= distance;
//       startPosition.value = e.clientX;
//     }
//   });
//   // 给父元素加上mouseup事件
//   containerRef.value?.addEventListener('mouseup', (e: MouseEvent) => {
//     e.preventDefault(); // 防止默认的选择行为
//     isDragging.value = false;
//     console.log(isDragging.value);
//   });
// });
</script>

<template>
  <div class="plan-container" ref="containerRef">
    <p class="title">定制化行业解决方案</p>

    <div class="main" ref="scrollWrapper">
      <!--      <span class="btn-container-left arrow" style="transform: rotate(180deg)">-->
      <!--        <img :src="ArrowLeft" width="28px" height="28px" />-->
      <!--      </span>-->
      <span
        @click="onBtnClick(index)"
        :class="{ 'btn-container': true, active: index === currentIndex }"
        v-for="(item, index) in btnList"
        :key="index"
      >
        {{ item.name }}
      </span>
      <!--      <span class="btn-container-right arrow">-->
      <!--        <img :src="ArrowRight" width="28px" height="28px" />-->
      <!--      </span>-->
    </div>
    <div class="main-title">
      {{ btnList[currentIndex].title }}
    </div>
    <div class="main-content">{{ btnList[currentIndex].detail }}</div>
    <div class="main-btn" v-if="btnList[currentIndex].showBtn">了解详情</div>
    <div class="main-demo">
      <span style="display: block; color: white">典型案例</span>
      <div style="background: hsla(0, 0%, 100%, 0.5); margin-top: 20px">
        <img
          :src="btnList[currentIndex].demo"
          min-width="200px"
          height="60px"
        />
      </div>
    </div>
    <el-carousel ref="planRef" trigger="click" height="150px" :autoplay="false">
      <el-carousel-item
        v-for="(item, index) in imgList"
        :key="index"
        style="display: block"
      >
        <div
          class="img-container"
          :style="{ backgroundImage: `url(${item})` }"
        ></div>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<style scoped lang="scss">
.plan-container {
  width: 100%;
  height: 724px;
  position: relative;
  .title {
    position: absolute;
    font-size: 32px;
    line-height: 50px;
    font-weight: 600;
    text-align: center;
    margin: 72px 0 43px;
    z-index: 1;
    color: white;
    left: 38%;
    top: 0;
  }
  .main {
    width: 80%;
    height: 40px;
    position: absolute;
    top: 24%;
    left: 10%;
    z-index: 1;
    white-space: nowrap; /* 防止换行 */
    overflow: hidden;
    -webkit-backdrop-filter: blur(2px);
    backdrop-filter: blur(2px);
    background: linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.16),
      rgba(0, 0, 0, 0.18)
    );
    .btn-container {
      color: white;
      width: 16.66666%;
      height: 40px;
      line-height: 40px;
      display: inline-block;
      text-align: center;
      cursor: pointer;
      font-size: 16px;
    }
    .btn-container.active {
      background-color: #cc0000;
    }
    //.arrow {
    //  color: white;
    //  width: 16.66666%;
    //  height: 40px;
    //  line-height: 40px;
    //  display: inline-block;
    //  text-align: center;
    //  cursor: pointer;
    //  font-size: 16px;
    //  z-index: 3;
    //}
    //.btn-container-left {
    //  img {
    //    margin-top: 6px;
    //  }
    //}
    //.btn-container-right {
    //  img {
    //    margin-top: 6px;
    //  }
    //}
  }
  .main-title {
    min-width: 300px;
    height: 33px;
    position: absolute;
    z-index: 1;
    top: 28%;
    left: 10%;
    font-weight: 600;
    font-size: 24px;
    line-height: 33px;
    margin: 52px 0 14px;
    color: white;
  }
  .main-content {
    position: absolute;
    z-index: 1;
    top: 42%;
    left: 10%;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    margin-bottom: 34px;
    max-width: 870px;
    width: 90%;
    height: 85px;
    overflow: auto;
    color: white;
  }
  .main-btn {
    position: absolute;
    z-index: 1;
    top: 52%;
    left: 10%;
    width: 120px;
    height: 40px;
    line-height: 40px;
    text-align: center;
    cursor: pointer;
    border-radius: 2px;
    border: 1px solid #fff;
    color: white;
    font-weight: 400;
    font-size: 14px;
    margin-bottom: 72px;
    display: inline-block;
  }
  .main-btn:hover {
    border: 1px solid red;
    color: red;
  }
  .main-demo {
    position: absolute;
    z-index: 1;
    top: 62%;
    left: 10%;
  }
  .el-carousel {
    height: 100%;
    width: 100%;
  }
  .img-container {
    width: 100%;
    height: 100%;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;
  }
  ::v-deep .el-carousel__arrow {
    display: none;
  }
  ::v-deep .el-carousel__item {
    display: block;
    width: 100%;
    height: 724px;
  }
  ::v-deep .el-carousel__indicators {
    display: none;
  }
}
</style>
