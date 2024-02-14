<script lang="ts" setup="">
import { onMounted, ref } from 'vue';

const customerList = [
  {
    count: '100+',
    name: '世界500强',
  },
  {
    count: '200+',
    name: '世界500强+',
  },
  {
    count: '1500+',
    name: '政务服务应用场景',
  },
  {
    count: '4500+',
    name: '生态伙伴',
  },
];
const tabList = [
  {
    tabName: '人力资源',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32910.jpg',
        text: '引入e签宝以后，平均我们每次入职的时间可以节省半小时以上，员工证明类的文件只需要在自助机上轻轻一点，10s钟就能拿到带着鲜红印章的证明文件，这不仅仅提高了我们员工的体验感，提高了HR的工作效率，同时也给公司节省了大量的成本。',
        GS: '——吉利汽车',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32946.jpg',
        text: '自从我们对接上了e签宝的体系，大大提升了HR的办理效率，遇到入职高峰期，可以给多位员工一键发起批量签署，上百份合同几分钟内就能签完。',
        GS: '——蓝月亮',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32912.jpg',
        text: '和e签宝合作极大地降低了人力部门日常操作纸质劳动合同签署的复杂度，提升了企业内部管理效能，对于员工来说操作步骤简单便捷，更容易查询保存。',
        GS: '——中国广核集团',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32913.jpg',
        text: '可以说电子合同在很大程度上助推了HR的工作效能，做到以数字科技驱动，满足不同企业的需求。',
        GS: '——金柚网',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35341.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35342.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35343.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35344.png',
    ],
  },
  {
    tabName: '物业/不动产开发',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32906.jpg',
        text: '电子签名技术不仅帮助我们实现了在线签署，还实现了档案的线上管理，不再占用大量的人力以及空间存储，我们把文件存储到云端，借助e签宝区块链技术的加成，使我们的档案管理更加安全高效。',
        GS: '——绿地香港',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32907.jpg',
        text: 'e签宝电子签名技术的引入，帮助我们大大降低了用印的安全合规风险，是企业从粗放到精细化数字化管理转型的毕竟环节。',
        GS: '——旭辉地产',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32908.jpg',
        text: '我们之所以选择e签宝合作，是因为其专业且灵活的解决方案，不仅符合业务需求，同时还打消了我们对于电子签在合规性、安全性及有效性的顾虑，上线后签约效率提升了10倍以上。',
        GS: '——正大集团',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32909.jpg',
        text: 'e签宝的在线起草、审批、多方签署等亮点功能实实在在地解决了物企在印章管理、招商租赁、服务工作中的盖章和签署难题，做到了降本增效。',
        GS: '——永升服务',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35346.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35347.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35348.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35349.png',
    ],
  },
  {
    tabName: '建筑',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32914.jpg',
        text: '我们在全国六百多个项目管理部，对我们这种大型施工企业来讲，印章管理是我们非常头疼的。有了e签宝后，现在基本上涉及到所有用印部分，电子签章都和我们的信息化系统匹配的很好，也极大地提高了我们印章/档案管理的时效性和安全性。',
        GS: '——苏中建设集团',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32915.jpg',
        text: '对于我们建筑施工企业来讲，有高效的电子签署的存在，会极大提高我们档案管理的时效性和安全性。',
        GS: '——中铁六局集团',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/20/32960.jpg',
        text: '电子签名服务不仅仅提高了业务流程效率，还打通了合同法务信息化建设的最后一公里，保证了签署过程的合法合规以及合同本身的法律效力。',
        GS: '——中交第一航务工程局',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35350.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35351.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35352.png',
    ],
  },

  {
    tabName: '银行保险',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32917.jpg',
        text: 'e签宝拥有成熟而丰富的银行业电子签名解决方案，促进我们业务办理效率提升，节省营运管理成本，保障文件签署安全性及合规性。',
        GS: '——华夏银行',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32918.jpg',
        text: 'e签宝电子签名降低业务运营成本，提高“邮惠付”业务的作业效率上起到了很大的作用。',
        GS: '——中国邮政储蓄银行',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32919.jpg',
        text: '通过引入电子签章，实现线下纸质流程和线上业务完全打通，解决新疆农信下辖82家行社信息化发展全程无纸化的最后一个难题，大大提高了区联社办事能力。',
        GS: '——新疆维吾尔自治区农村信用社联合社',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32920.jpg',
        text: '投保函不需要再来回邮寄，只需要投保人和业务经理远程签署，提高了用户的服务体验和满意度。',
        GS: '——中国人寿',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35353.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35354.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35355.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35356.png',
    ],
  },
  {
    tabName: '制造业',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32921.jpg',
        text: '拿供应链采购场景举例，从前需要通过线下邮寄盖章来完成合同签署，自从引入e签宝后，每年在合同上投入的纸张耗材、邮寄费用、人员成本从几百万下降到了几十万，合同签署周期也从15天左右缩短到了一天以内,真正实现了降本增效。',
        GS: '——海康威视',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32922.jpg',
        text: '新零售的趋势是人群细分、渠道细分、以及用户需求的多样化，为小家电市场注入了新的机会点。在数字升级的过程中，九阳引入e签宝的电子签名技术，用电子合同将采购、经销、物流等业务场景高效串联起来，提升了供应链的灵活协同能力，让我们在探索新零售的路上始终保持领先。',
        GS: '——九阳',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32923.jpg',
        text: '电子签名技术的引入掉了来回邮寄、盖章的时间，合同当天签完当天就能发货，大幅提升了我们供应链的流转效率。',
        GS: '——浙江大华技术股份有限公司',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35357.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35358.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35359.png',
    ],
  },
  {
    tabName: '快消零售业',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32924.jpg',
        text: '新零售时代，年轻人的消费需求不断升级，数字化创新成为了快消品企业快速发展的必修课。 我们江小白酒业早在2019年就与e签宝建立了合作。现在，e签宝的电子签名服务已成为公司业务协同和运营决策的一大助力，让我们清晰地看到了数字化升级带来的效果。',
        GS: '——江小白',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32925.jpg',
        text: '飞鹤为了企业的数字化转型做了大量的工作，引入e签宝电子签名就是其中之一，实现了劳动合同、经销商协议的在线签署，为业务的高效运转保驾护航。',
        GS: '——飞鹤乳业',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32926.jpg',
        text: '经销商对接以及人力资源管理工作涉及的合同数量庞大，纸质合同的工作量不容小觑。同时，合同签署场景虽小，却关联着业务、财务、法务等众多环节，e签宝为天味提供了非常便捷、安全的电子签名解决方案，希望通过与e签宝的合作，提升天味的内部管理效率，实现全场景数字化。',
        GS: '——天味食品',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32927.jpg',
        text: '作为商源集团旗下酒水流通品牌，我们已与e签宝达成合作，将在供应链采购、商品经销、人力资源管理等场景引入e签宝的电子签名服务，双方共同推进企业数字化升级，在酒水流通行业形成示范。',
        GS: '——久加久',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35360.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35361.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35362.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35363.png',
    ],
  },
  {
    tabName: '公共服务',
    swiper: [
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32928.jpg',
        text: '作为“最多跑一次”指定电子签供应商，在省内范围内打造了统一电子平台，真正做到“让数据多跑路，让群众少跑腿”。',
        GS: '——浙江省大数据发展管理局',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32929.jpg',
        text: '中国互联网电子签名行业领跑者e签宝与专注服务“互联网+政企采购”的云服务企业——政采云强强联手，共同助力青海省财政厅实现招投标场景全流程业务线上办理。',
        GS: '——青海省财政厅',
      },
      {
        url: 'https://www.esign.cn/upload/resources/file/2022/05/19/32931.jpg',
        text: 'e签宝旗下金格科技助力江西省生态环境厅，构建了数字政务一体化平台，实现了全省环境部门的电子文档编辑、公文交换、档案管理、电子签章等信创化改造，在数字政务领域跨入全国前列。',
        GS: '——江西省生态环境厅',
      },
      {
        url: 'https://www.esign.cn/upload/resources/image/2023/09/21/39535.jpg',
        text: '通过引入e签宝的电子签名系统，浙大四院重塑了整个就诊流程，所有签名环节都能在线完成并具有法律效应。对医生来说，电子签提高了工作效率，对患者来说，电子签不仅更方便，也更好地保护了个人隐私。',
        GS: '——浙江大学医学院附属第四医院',
      },
    ],
    icon: [
      'https://www.esign.cn/upload/resources/image/2023/06/20/35364.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35365.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35366.png',
      'https://www.esign.cn/upload/resources/image/2023/06/20/35367.png',
    ],
  },
];
const tabItemRef = ref();
const currentIndex = ref(0);
const onTabClick = (index: number) => {
  currentIndex.value = index;
  swiperIndex.value = 0; //切换tab时候 对应轮播图从0开始
  console.log('cur', currentIndex.value);
  if (tabItemRef.value[index]) {
    tabItemRef.value[index].classList.add('active');
  }
  // 排他
  const arr = [0, 1, 2, 3, 4, 5, 6].filter((item) => item !== index);
  arr.forEach((item) => {
    if (tabItemRef.value[item]) {
      tabItemRef.value[item].classList.remove('active');
    }
  });
};
onMounted(() => {
  onTabClick(0); //初始化
});
const swiperIndex = ref<number>(0);
const swiperChange = (event: any) => {
  swiperIndex.value = event; //对应当前tab下轮播图下标
};
const bottomImgList = [
  'https://www.esign.cn/upload/resources/file/2022/12/29/34985.png',
  'https://www.esign.cn/upload/resources/file/2022/05/19/32933.png',
];
// 实现滚动
</script>

<template>
  <div class="choose-container">
    <p class="choose-title">更多客户选择使用e签宝</p>
    <div class="choose-customer">
      <div
        class="choose-customer-item"
        v-for="(item, index) in customerList"
        :key="index"
      >
        <span class="choose-customer-item-left">{{ item.count }}</span>
        <span class="choose-customer-item-right">{{ item.name }}</span>
      </div>
    </div>
    <div class="choose-tab">
      <div
        class="choose-tab-item"
        v-for="(item, index) in tabList"
        :key="index"
        ref="tabItemRef"
        @click="onTabClick(index)"
      >
        {{ item.tabName }}
      </div>
    </div>
    <div class="choose-main" v-for="(item, index) in tabList" :key="index">
      <template v-if="index === currentIndex">
        <div class="choose-main-left">
          <el-carousel height="422px" :autoplay="true" @change="swiperChange">
            <el-carousel-item
              v-for="(swiperItem, index) in item.swiper"
              :key="index"
              style="display: block"
            >
              <div
                class="swiper-img"
                :style="{
                  'background-image': `url(${swiperItem.url})`,
                }"
              ></div>
            </el-carousel-item>
          </el-carousel>
          <div
            class="bottom-icon"
            :style="{ 'background-image': `url(${item.icon[swiperIndex]})` }"
          >
            <div
              style="display: flex; height: 80px; width: 25%"
              v-for="i in item.swiper.length"
              :key="i"
            ></div>
          </div>
        </div>
        <div class="choose-main-right">
          <div
            v-for="(j, index) in item.swiper"
            :key="index"
            style="margin-top: 80px"
          >
            <div class="choose-main-right-text" v-if="swiperIndex === index">
              {{ j.text }}
            </div>
            <div class="choose-main-right-GS" v-if="swiperIndex === index">
              {{ j.GS }}
            </div>
          </div>
        </div>
      </template>
    </div>
    <div class="choose-bottom-img" style="overflow: hidden">
      <div
        v-for="(item, index) in bottomImgList"
        :key="index"
        class="bottom-img-item"
      >
        <img :src="item" width="250%" height="100%" />
      </div>
    </div>
    <div style="margin: 30px 0">
      <div style="cursor: pointer">
        <a
          href="https://www.esign.cn/site/customer-case"
          style="color: #cc0000"
        >
          更多客户案例>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
a {
  text-decoration: none; //去除下划线
}
.choose-container {
  width: 100%;
  //height: 870px;
  display: flex;
  align-items: center;
  flex-direction: column;
  .choose-title {
    text-align: center;
    margin-bottom: 30px;
    font-size: 32px;
    font-family:
      PingFangSC-Medium,
      PingFang SC;
    font-weight: 600;
    color: rgba(0, 0, 0, 0.85);
    line-height: 50px;
  }
  .choose-customer {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 78px;
    background: #f5f5f5;
    cursor: default;
    .choose-customer-item {
      margin: 0 40px;
      .choose-customer-item-left {
        width: 80px;
        height: 50px;
        font-size: 30px;
        font-family:
          PingFangSC-Semibold,
          PingFang SC;
        font-weight: 600;
        color: #c00;
        line-height: 50px;
      }
      .choose-customer-item-right {
        width: 136px;
        height: 28px;
        font-size: 20px;
        font-family:
          PingFangSC-Regular,
          PingFang SC;
        font-weight: 400;
        color: #000;
        line-height: 28px;
      }
    }
  }
  .choose-tab {
    width: 100%;
    height: 42px;
    display: flex;
    margin-top: 42px;
    margin-bottom: 32px;
  }
  .choose-tab-item {
    flex: 1;
    text-align: center;
    font-size: 16px;
    font-family:
      PingFangSC-Regular,
      PingFang SC;
    font-weight: 400;
    color: #333;
    line-height: 22px;
    cursor: default;
    padding-bottom: 30px;
  }
  .choose-tab-item:hover {
    color: red;
  }
  .choose-tab-item.active {
    color: red;
    border-bottom: 4px solid red;
  }
  .choose-main {
    width: 100%;
    display: flex;
    .choose-main-left {
      width: 50%;
      height: 422px;
      position: relative;
      .swiper-img {
        width: 100%;
        height: 100%;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: right center;
      }
      .bottom-icon {
        position: absolute;
        width: 100%;
        height: 80px;
        bottom: 0;
        background-position: right center;
        background-repeat: no-repeat;
        background-size: 80% 100%;
        background-color: rgba(white, 0.8);
        display: flex;
      }
    }
    .choose-main-right {
      width: 50%;
      height: 422px;
      background: #cc0000;
      .choose-main-right-text {
        font-size: 16px;
        font-family:
          PingFangSC-Regular,
          PingFang SC;
        font-weight: 400;
        color: #fff;
        line-height: 28px;
        padding-left: 40px;
        max-width: 500px;
      }
      .choose-main-right-GS {
        font-size: 16px;
        font-family:
          PingFangSC-Regular,
          PingFang SC;
        font-weight: 400;
        color: #fff;
        line-height: 28px;
        padding-left: 40px;
        margin-top: 20px;
      }
    }
  }

  .bottom-img-item {
    margin: 10px;
    width: 100%;
    height: 80px;
    background-repeat: repeat;
    background-position: 50% 50%;
    background-size: cover;
    display: flex;
    align-items: center; /* 垂直居中 */
  }
  .bottom-img-item:nth-child(1) {
    justify-content: left; /* 右 */
    animation: scrollLeft 200s linear infinite; /* 向左滚动，100秒完成一次循环 */
  }
  .bottom-img-item:nth-child(2) {
    justify-content: right; /* 左 */
    animation: scrollRight 200s linear infinite; /* 向右滚动100秒完成一次循环 */
  }
  @keyframes scrollLeft {
    0% {
      transform: translateX(10%);
    }
    100% {
      transform: translateX(-150%);
    }
  }

  @keyframes scrollRight {
    0% {
      transform: translateX(-10%);
    }
    100% {
      transform: translateX(150%);
    }
  }

  //::v-deep .el-carousel__arrow {
  //  display: none;
  //}
  ::v-deep .el-carousel__indicators {
    display: none;
  }
}
</style>
