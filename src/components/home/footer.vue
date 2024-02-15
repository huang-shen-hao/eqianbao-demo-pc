<script lang="ts" setup="">
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
</script>

<template>
  <div class="footer-container">
    <div class="footer-container-our"></div>
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
    min-height: 400px;
    background: #242424;
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
