<script lang="ts" setup="">
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
  </div>
</template>

<style scoped lang="scss">
.choose-container {
  width: 100%;
  height: 870px;
  background: #e16969;
  margin-top: 30px;
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
}
</style>
