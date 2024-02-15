<script lang="ts" setup=""></script>

<template>
  <div class="form-container">
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
  </div>
</template>

<style scoped lang="scss">
.form-container {
  width: 100%;
  height: 100px;
  background-color: #676262;
  display: flex;
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
}
</style>
