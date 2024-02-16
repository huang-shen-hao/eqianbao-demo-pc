<script lang="ts" setup="">
import { onMounted, ref } from 'vue';
let isStick = ref<boolean>(false);
const scrollFun = () => {
  console.log(
    '1999',
    document.documentElement.scrollHeight,
    window.innerHeight,
    window.scrollY,
  );
  // 距离底部距离
  let scrollDistanceToBottom =
    document.documentElement.scrollHeight - window.innerHeight - window.scrollY;
  if (scrollDistanceToBottom >= 545 && scrollDistanceToBottom <= 2000) {
    isStick.value = true;
  } else {
    isStick.value = false;
  }
};
onMounted(() => {
  // Element.scrollHeight 只读属性是一个元素内容高度的度量，包括由于溢出导致的视图中不可见内容。
  // window.innerHeight 浏览器窗口的视口（viewport）高度（以像素为单位）；如果有水平滚动条，也包括滚动条高度。
  // window.scrollY返回文档在垂直方向已滚动的像素值。
  window.addEventListener('scroll', scrollFun);
});
const formRef = ref();
const onClose = () => {
  isStick.value = false;
  window.removeEventListener('scroll', scrollFun); //关闭以后就不会再监听了
};
</script>

<template>
  <div
    class="form-container"
    :style="isStick ? { position: 'sticky', bottom: '0' } : {}"
    ref="formRef"
  >
    <div class="form-container-left">
      <div class="elephant">
        <img
          src="https://asset.tsign.cn/apps/esign/esign-website-ssr/prod/img/qxx.e90690c.png"
        />
      </div>
    </div>
    <div class="form-container-right">
      <div class="text">
        <div class="phone">销售热线：0571-85785223</div>
        <div class="check">
          <input type="checkbox" />
          <span style="padding-left: 2px; color: white; font-size: 14px">
            我已阅读并同意
          </span>
          <span style="color: #1890ff; font-size: 14px">《隐私政策》</span>
        </div>
      </div>
      <div class="input">
        <div class="input-item" style="width: 80px">
          <input class="input-item" placeholder="您的姓名" />
        </div>
        <div class="input-item" style="width: 160px">
          <input placeholder="公司名称" />
        </div>
        <div class="input-item" style="width: 120px">
          <input placeholder="手机号码" />
        </div>
        <div class="input-item" style="position: relative; width: 190px">
          <input style="width: 80px" placeholder="验证码" />
          <div
            class="yanzhengma"
            style="
              position: absolute;
              left: 76px;
              top: 0;
              background: #efefef;
              color: red;
              border-radius: 2px;
              height: 30px;
              line-height: 30px;
              text-align: center;
              width: 100px;
              font-size: 14px;
              cursor: pointer;
            "
          >
            获取验证码
          </div>
        </div>
        <div class="btn">
          <div>免费试用</div>
        </div>
      </div>
    </div>
    <div v-if="isStick" class="close" @click="onClose">
      <img
        src="https://trial-cdn.esign.cn/upload/28d7c1c8-c54b-509d-9e17-a0086c340676!!5-16.png"
      />
    </div>
  </div>
</template>

<style scoped lang="scss">
.form-container {
  width: 100%;
  height: 100px;
  background-color: #676262;
  display: flex;
  position: relative;
  .form-container-left {
    width: 20%;
    height: 100%;
    position: relative;
    .elephant {
      width: 180px;
      height: 180px;
      position: absolute;
      right: -50px;
      top: -50px;
      img {
        width: 100%;
        height: 100%;
      }
    }
  }
  .form-container-right {
    width: 80%;
    height: 100px;
    .text {
      width: 100%;
      height: 50px;
      box-sizing: border-box;
      display: flex;
      align-items: center;
      justify-content: left;
      padding-left: 60px;
      .phone {
        height: 50px;
        line-height: 50px;
        color: white;
        font-size: 30px;
      }
      .check {
        width: 250px;
        height: 50px;
        line-height: 50px;
        display: flex;
        align-content: center;
        margin-left: 215px;
        //background-color: #cc0000;
      }
    }
    .input {
      width: 100%;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: left;
      box-sizing: border-box;
      padding-left: 60px;
      .input-item {
        margin-right: 10px;
        input {
          width: 100%;
          border: 1px solid transparent;
          outline: unset;
          background: #efefef;
          border-radius: 2px;
          height: 30px;
          line-height: 30px;
          box-sizing: border-box;
          padding-left: 10px;
          font-size: 14px;
        }
      }
      .btn {
        width: 120px;
        height: 30px;
        line-height: 30px;
        font-size: 14px;
        text-align: center;
        color: #fff;
        background: #c00;
        border-radius: 2px;
        font-weight: 400;
        cursor: pointer;
      }
    }
  }
  .close {
    position: absolute;
    width: 30px;
    height: 30px;
    right: 20px;
    top: 10px;
    img {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
