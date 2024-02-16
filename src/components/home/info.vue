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
const infoList = [
  {
    title:
      '省民建数字经济专委会正式成立共谋产业数字化，e签宝CEO金宏洲任本届专委会主任',
    content:
      '1月17日，省民建企业家协会数字经济专委会成立会议暨“AI浪潮下，数字时尚产业发展之道”论坛在杭州钱塘区顺利召开。',
    date: '2024-01-23',
  },
  {
    title: '重磅！追加跟投幂律智能融资8000万，e签宝继续加码智能合同管理',
    content:
      'e签宝近日参与跟投的幂律智能宣布完成近8000万元Pre-B融资，幂律智能是一家专注于法律领域的人工智能公司，该轮由蓝驰创投领投，跟投机构中还包括红杉中国、华宇科创、源码资本、线性资本、智谱AI等。追加跟投幂律智能，意味着e签宝布局AI合同管理的底气。',
    date: '2023-12-08',
  },
  {
    title: '重磅｜e签宝电子签名通过中国证监会信息技术系统服务备案',
    content:
      '最新消息，e签宝（杭州天谷信息科技有限公司）已成功完成中国证监会信息技术系统服务备案，与阿里云计算、工业信息安全发展研究中心等8家机构一同被公布为新一批通过备案的信息技术系统服务机构。(注：中国证券监督管理委员会是国务院直属机构，依照法律、法规和国务院授权，统一监督管理全国证券期货市场，维护证券期货市场秩序',
    date: '2023-11-15',
  },
  {
    title:
      'e签宝专家团参编｜《第三方电子合同服务平台信息安全技术要求》明年4月实施',
    content:
      '《第三方电子合同服务平台信息安全技术要求》将于2024年4月1日起正式开始实施。此国标是由国家市场监督管理总局联合国家标准化管理委员会发布。e签宝作为主要起草单位，e签宝创始人兼CEO金宏洲携COO程亮等技术专家组共计四人担任主要起草人参与其中。',
    date: '2023-11-02',
  },
  {
    title:
      '守好合规生命线,紧抓网络安全与数据保护，e签宝荣登“浙江省网络安全规模十强企业',
    content:
      '16%，同比增长10.26%；网络安全服务收入24.83亿元，占总收入的15.44%，同比增长19.09%；网络安全综合业务收入7.07亿元，占总收入的4.4%。报告以省内重点原厂安全能力企业调查数据为支撑，入选的“浙江省网络安全规模十强企业”代表着浙江省网络安全产业的领先力量。',
    date: '2023-09-12',
  },
  {
    title: '走进小罐茶！走进名企第二站:电子合同助力快消行业数字化转型',
    content:
      '6月份，e签宝启动了“走进名企系列沙龙”活动。活动开展的背景，是在司法对电子证据提出更高要求的前提下，更好地让中国各企业的法总，规避法律风险、快速溯源、有效举证。 7月16日，“走进名企系列沙龙”的第二站来到安徽黄山',
    date: '2023-07-19',
  },
  {
    title: '法总面对面：走进e签宝，了解印章管理的挑战与最新解决方案！',
    content:
      '随着互联网的快速发展，新兴的商业模式带来了许多机遇，但合规风险也接踵而至。面对互联网新商业模式，传统企业印章管理办法产生的问题日渐显现：印章存放位置难以追踪；具有盖章权限的人员难以确认；印章的安全性难以保障。 寻求新的印章管理解决方案，规避潜在合规风险，成为许多企业，尤其是企业法务部门的当务之急。',
    date: '2023-07-07',
  },
  {
    title: '信创战队集结完毕，国产化电子签名就选e签宝',
    content: '18851977115',
    date: '2023-03-16',
  },
  {
    title: '人事场景中，智能合同如何助力企业复工满产？',
    content: '18851977115',
    date: '2023-03-01',
  },
];
// 记录当前index
const currentIndex = ref<number>(0);
const paginationRef = ref(); //轮播图指示器
const onImgChange = (e: any) => {
  currentIndex.value = e;
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
  carouselRef.value && carouselRef.value.setActiveItem(index);
};
onMounted(() => {
  onImgChange(0);
});
const rightScrollRef = ref(); //滚动元素
let activeIndex = ref<number>(0); //展示元素index
const showItem = ref<any>({
  title: '',
  content: '',
  date: '',
}); //拿到需要展示的数据
const onScroll = () => {
  // 每次都清空一下
  showItem.value.title = '';
  showItem.value.content = '';
  showItem.value.date = '';
  // 初始向上移动一个元素高度
  // if (rightScrollRef.value) {
  //   rightScrollRef.value.style.marginTop = '-73px';
  // }
  console.log('sss', rightScrollRef.value.scrollTop);
  const scrollDistance = rightScrollRef.value.scrollTop + 73; //记录滚动距离 加上73是显示第一个
  const elementHeight = 70; // 每个元素的高度
  const index = Math.floor(scrollDistance / elementHeight); // 计算第几个元素
  console.log('pp', index);
  // 向上滚的逻辑
  activeIndex.value = index - 1; //记录一下
  // console.log('kkk', scrollDistance);
  showItem.value.title = infoList[activeIndex.value].title; //拿到当前数据
  showItem.value.content = infoList[activeIndex.value].content; //拿到当前数据
  showItem.value.date = infoList[activeIndex.value].date; //拿到当前数据
};
onMounted(() => {
  onScroll();
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
      <div class="info-container-main-right">
        <!--主体展示-->
        <div class="main-right-show">
          <p class="main-right-show-title">{{ showItem.title }}</p>
          <p class="main-right-show-content">{{ showItem.content }}</p>
          <!--日期-->
          <div
            style="display: flex; position: absolute; right: 50px; bottom: 50px"
          >
            <div
              style="
                font-size: 32px;
                font-weight: 600;
                color: rgba(0, 0, 0, 0.65);
                line-height: 32px;
                margin-right: 4px;
              "
            >
              <span>{{ showItem.date.split('-')[2] }}/</span>
            </div>
            <div
              style="
                width: 34px;
                font-size: 14px;
                font-weight: 700;
                color: rgba(0, 0, 0, 0.65);
                line-height: 17px;
              "
            >
              <span>{{ showItem.date.split('-')[1] }}月</span>
              <br />
              <span>{{ showItem.date.split('-')[0] }}</span>
            </div>
          </div>
          <!--了解更多-->
          <div
            style="
              font-size: 14px;
              font-weight: 400;
              line-height: 20px;
              color: #c00;
              cursor: pointer;
            "
          >
            了解更多>
          </div>
        </div>
        <!--下面滚动的-->
        <div
          class="main-right-scroll"
          ref="rightScrollRef"
          @scrollend="onScroll"
        >
          <div
            class="main-right-scroll-item"
            v-for="(item, index) in infoList.slice(1)"
            :key="index"
          >
            <div class="right-title">{{ item.title }}</div>
            <div class="right-date">{{ item.date }}</div>
          </div>
        </div>
      </div>
    </div>
    <div style="margin: 30px 0">
      <div style="cursor: pointer">
        <a href="https://www.esign.cn/pcgw/gywm/gsxw/" style="color: #cc0000">
          更多资讯>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
a {
  text-decoration: none; //去除下划线
}
.info-container {
  width: 100%;
  background: url('https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/info-bg.a064ff0.jpg')
    no-repeat 50% center;
  background-size: cover;
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
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
    display: flex;
    .info-container-main-left {
      width: 40%;
      height: 332px;
      .info-container-main-left-text {
        width: 100%;
        height: 68px;
        box-sizing: border-box;
        background: #fff;
        padding-left: 30px;
        box-shadow: 0 2px 10px 0 hsla(0, 0%, 88.2%, 0.5);
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
    .info-container-main-right {
      height: 400px;
      //background-color: #cc0000;
      margin-left: 10px;
      box-sizing: border-box;
      background-color: white;
      .main-right-show {
        box-sizing: border-box;
        padding: 30px 20px;
        height: 172px;
        box-shadow: 0px 4px 5px -2px rgba(238, 230, 230, 0.75);
        position: relative;
        .main-right-show-title {
          font-size: 20px;
          font-weight: 400;
          color: rgba(0, 0, 0, 0.85);
          line-height: 28px;
          margin-bottom: 14px;
          margin-top: -10px;
        }
        .main-right-show-content {
          width: 70%;
          height: 40px;
          font-size: 14px;
          font-weight: 400;
          color: rgba(0, 0, 0, 0.65);
          line-height: 20px;
          overflow: hidden;
          -webkit-line-clamp: 2;
          -webkit-box-orient: vertical;
          display: -webkit-box;
          text-overflow: ellipsis;
        }
      }
      .main-right-scroll {
        height: calc(100% - 172px);
        overflow: auto;
        .main-right-scroll-item {
          box-sizing: border-box;
          padding: 0 10px;
          height: 73px;
          background-color: white;
          display: flex;
          justify-content: space-between;
          border-bottom: 1px solid #ededed;
          .right-title {
            height: 73px;
            line-height: 73px;
            text-align: left;
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
            max-width: 70%;
          }
          .right-date {
            min-width: 60px;
            font-size: 14px;
            font-weight: 400;
            color: rgba(0, 0, 0, 0.45);
            line-height: 73px;
            font-family: DINCondensed-Bold\, DINCondensed;
          }
        }
        //最后一个不需要底部线
        .main-right-scroll-item:last-child {
          border-bottom: 1px solid white;
        }
      }
    }
  }
  ::v-deep .el-carousel__indicators {
    display: none;
  }
}
</style>
