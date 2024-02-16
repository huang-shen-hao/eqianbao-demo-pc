<script lang="ts" setup="">
import {
  UserFilled,
  PhoneFilled,
  Stamp,
  SwitchFilled,
  CaretTop,
} from '@element-plus/icons-vue';
import { onMounted, ref } from 'vue';

const userRef = ref();
const phoneRef = ref();
let userTag = ref<boolean>(false);
let phoneTag = ref<boolean>(false);
const onUserEnter = () => {
  if (userRef.value) {
    userRef.value.style.display = 'block';
  }
};
const onUserLeave = () => {
  userTag.value = false;
  if (userRef.value) {
    userRef.value.style.display = 'none';
  }
};
const onPhoneEnter = () => {
  if (phoneRef.value) {
    phoneRef.value.style.display = 'block';
  }
};
const onPhoneLeave = () => {
  phoneTag.value = false;
  if (phoneRef.value) {
    phoneRef.value.style.display = 'none';
  }
};
const onLeave = (type: string) => {
  // 先判断用户是否移动到小框上
  setTimeout(() => {
    if (type === 'user') {
      if (userTag.value) return; //用户移动到小框上了
      if (userRef.value) {
        userRef.value.style.display = 'none';
      }
    }
    if (type === 'phone') {
      if (phoneTag.value) return; //用户移动到小框上了
      if (phoneRef.value) {
        phoneRef.value.style.display = 'none';
      }
    }
  }, 100);
};
const showTop = ref<boolean>(false); //控制显示 回到顶部
onMounted(() => {
  window.addEventListener('scroll', function () {
    const scrollDistance = window.scrollY || document.documentElement.scrollTop;

    if (scrollDistance >= 1000) {
      showTop.value = true;
    } else {
      showTop.value = false;
    }
  });
});
const backTop = () => {
  window.scroll({
    top: 0,
    behavior: 'smooth', // 可选，实现平滑滚动
  });
};
</script>

<template>
  <div class="tool-container">
    <div class="tool-item">
      <div @mouseleave="onLeave('user')" @mouseenter="onUserEnter">
        <el-icon><UserFilled /></el-icon>
        <br />
        <span>在线客服</span>
      </div>
    </div>
    <div class="tool-item">
      <div @mouseleave="onLeave('phone')" @mouseenter="onPhoneEnter">
        <el-icon><PhoneFilled /></el-icon>
        <br />
        <span>电话咨询</span>
      </div>
    </div>
    <div class="tool-item">
      <el-icon><Stamp /></el-icon>
      <br />
      <span>查看合同</span>
    </div>
    <div class="tool-item">
      <el-icon><SwitchFilled /></el-icon>
      <br />
      <span>微信咨询</span>
    </div>
    <div @click="backTop" v-show="showTop" class="go-to-top">
      <el-icon><CaretTop /></el-icon>
    </div>
    <div
      @mouseenter="userTag = true"
      @mouseleave="onUserLeave"
      ref="userRef"
      class="user-container"
    >
      <div class="user-container-item">
        <div>
          <img
            src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/kefu-shouqian.8d6eb73.png"
          />
        </div>
        <div class="user-container-item-right">
          <div class="user-container-item-title">售前客服咨询</div>
          <div class="user-container-item-text">客服一对一在线沟通</div>
        </div>
      </div>
      <div class="user-container-item">
        <div>
          <img
            src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/kefu-shouhou.4a1881d.png"
          />
        </div>
        <div class="user-container-item-right">
          <div class="user-container-item-title">使用问题咨询</div>
          <div class="user-container-item-text">提供售后咨询服务</div>
        </div>
      </div>
    </div>
    <div
      @mouseenter="phoneTag = true"
      @mouseleave="onPhoneLeave"
      ref="phoneRef"
      class="phone-container"
    >
      <div class="phone-container-item">
        <div>
          <img
            src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/tel-shouqian.3f6ae0c.png"
          />
        </div>
        <div class="phone-container-right">
          <div class="phone-container-title">销售热线</div>
          <div class="phone-container-text">0571-85785223</div>
        </div>
      </div>
      <div class="phone-container-item">
        <div>
          <img
            src="//asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/tel-shouhou.ee6174f.png"
          />
        </div>
        <div class="phone-container-right">
          <div class="phone-container-title">销售服务</div>
          <div class="phone-container-text">400-0878-198</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.tool-container {
  width: 84px;
  height: 360px;
  position: fixed;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  z-index: 100001;
  display: flex;
  flex-direction: column;
  align-items: flex-end; //右侧
  .tool-item {
    width: 60px;
    height: 40px;
    position: relative;
    background-color: white;
    text-align: center;
    margin: 10px 0;
    word-break: break-all;
    font-size: 14px;
    font-weight: 400;
    line-height: 18px;
    color: #999999;
    padding: 8px;
    transition:
      width 0.3s linear,
      background-color 0.3s linear;
  }
  .tool-item:hover {
    background-color: #cc0000;
    width: 80px;
    color: white;
  }
  .go-to-top {
    width: 60px;
    height: 20px;
    background-color: white;
    text-align: center;
    margin: 10px 0;
    color: #999999;
    padding: 8px;
    transition: background-color 0.3s linear;
  }
  .go-to-top:hover {
    color: white;
    background-color: #cc0000;
  }
  .phone-container {
    position: absolute;
    width: 200px;
    height: 150px;
    display: none;
    background-color: white;
    left: -214px;
    top: 86px;
    box-sizing: border-box;
    padding: 6px;
    .phone-container-item {
      display: flex;
      border: 2px solid rgba(238, 238, 241, 0.6);
      height: 60px;
      margin-bottom: 10px;
      border-radius: 4px;
      cursor: pointer;
      img {
        width: 60px;
        height: 60px;
      }
      .phone-container-right {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        .phone-container-title {
          color: #000000;
          font-size: 14px;
        }
        .phone-container-text {
          color: #999999;
          font-size: 12px;
        }
        .phone-container-title:hover {
          color: red;
        }
        .phone-container-text:hover {
          color: red;
        }
      }
    }
  }
  .user-container {
    position: absolute;
    width: 200px;
    height: 150px;
    background-color: white;
    left: -214px;
    top: 10px;
    display: none;
    box-sizing: border-box;
    padding: 6px;
    .user-container-item {
      display: flex;
      border: 2px solid rgba(238, 238, 241, 0.6);
      height: 60px;
      margin-bottom: 10px;
      border-radius: 4px;
      cursor: pointer;
      img {
        width: 60px;
        height: 60px;
      }
      .user-container-item-right {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        .user-container-item-title {
          color: #000000;
          font-size: 14px;
        }
        .user-container-item-title:hover {
          color: #cc0000;
        }
        .user-container-item-text {
          color: #999999;
          font-size: 12px;
        }
      }
    }
  }
}
</style>
