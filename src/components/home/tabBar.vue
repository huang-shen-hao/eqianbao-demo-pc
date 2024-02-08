<script setup lang="ts">
// 顶部菜单名称


import { ref, Ref } from 'vue'

// 顶部右侧菜单
const topMenu = [{
	name: '查看价格',
	href: 'https://www.esign.cn/site/quotation',
},
{
	name: '登录',
	href: 'https://h5.esign.cn/usercenterFront/login',
},
{
	name: '注册',
	href: 'https://h5.esign.cn/usercenterFront/regist?pub=esign',
}]
const jump = (address:string) => {
	window.location.href = address//跳转
}
// 几个二维码
const qrType = [
	{
		type: '微信端',
		title: '使用微信扫一扫',
		picUrl: 'https://www.esign.cn/upload/resources/image/2020/09/10/29066.png?1651743977350',
		icon: 'iconfont icon-weixin-copy',
	},
	{
		type: '支付宝',
		title: '使用支付宝扫一扫',
		picUrl: 'https://www.esign.cn/upload/resources/image/2020/09/10/29072.png?1651743977354',
		icon: 'iconfont icon-zhifubao',
	},
	{
		type: 'IOS版本',
		title: '扫一扫下载IOS客户端',
		picUrl: 'https://www.esign.cn/upload/resources/image/2021/12/27/32251.png?1651743977358',
		icon: 'iconfont icon-ios',
	},
	{
		type: '安卓版',
		title: '扫一扫下载安卓客户端',
		picUrl: 'https://www.esign.cn/upload/resources/image/2022/04/28/32543.png?1651743977362',
		icon: 'iconfont icon-anzhuo',
	},
	{
		type: '钉钉端',
		title: '使用钉钉扫一扫',
		picUrl: 'https://www.esign.cn/upload/resources/image/2020/09/10/29075.png?1651743977366',
		icon: 'iconfont icon-dingding',
	},
	{
		type: '客户端',
		title: '点击打开客户端下载页',
		picUrl: 'https://www.esign.cn/upload/resources/image/2021/09/24/31942.png?1651743977369',
		icon: 'iconfont icon-client2',
	},
]

const qrItems = ref<HTMLElement[] | null>(null)
// 第一个默认
const onHover = () => {
	if(qrItems.value) {
		console.log('ppppp', qrItems.value[0])
		qrItems.value[0].style.backgroundColor = 'white'
		qrItems.value[0].style.borderLeft = '2px solid red'
		const icon = qrItems.value[0].querySelector('.QrCode_left_item_icon')
		const pic = qrItems.value[0].querySelector('.pic')
		if(icon) 	icon.style.backgroundColor = 'green'
		if(pic) pic.style.display = 'block'

		console.log('ppp', icon, pic)
	}
}
const changeBackground = (index: number) => {
	console.log('ppppp', index, qrItems.value)
	// 针对第一个默认选中 当其他选中时 去除第一个默认选中的样式
	if (index !== 0 &&  qrItems.value ) {
		qrItems.value[0].style.backgroundColor = '#f3efef'
		qrItems.value[0].style.borderLeft = '2px solid #f3efef'
	}
	if (index === 0 &&  qrItems.value ) {
		qrItems.value[0].style.backgroundColor = 'white'
		qrItems.value[0].style.borderLeft = '2px solid red'
	}

}
const resetBackground = () => {
	if(qrItems.value) qrItems.value[0].style.backgroundColor = '' // 或者恢复默认的背景颜色
}
</script>

<template>
  <div class="container">
    <div class="top">
      <!--左侧图片-->
      <div class="top_left">
        <a href="https://www.esign.cn/">
          <img
            src="@/assets/e签宝.png"
            alt="e签宝"
          >
        </a>
      </div>
      <!--右侧菜单-->
      <div class="top_right">
        <div class="top_right_item QrCode_show">
          <span @mouseover="onHover">客户端/小程序/APP</span>
          <div class="QrCode">
            <div
              class="QrCode_left"
            >
              <!--左侧类型-->
              <div
                :class="{ QrCode_left_item: true, firstItem: index === 0 }"
                v-for="(item,index) in qrType"
                :key="item.type"
                @mouseover="changeBackground(index)"
                @mouseout="resetBackground"
                ref="qrItems"
              >
                <div class="QrCode_left_item_icon">
                  <i :class="item.icon" />
                </div>
                <div style="color: black">
                  {{ item.type }}
                </div>
                <!--右侧图片-->
                <div class="pic">
                  <div>
                    <img
                      :src="item.picUrl"
                      width="200"
                      height="200"
                    >
                  </div>
                  <div style="color: #999999">
                    {{ item.title }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div
          class="top_right_item"
          v-for="item in topMenu"
          :key="item.name"
        >
          <span
            style="cursor:pointer;"
            @click="jump(item.href)"
          >
            {{ item.name }}
          </span>
        </div>
        <el-button class="top_button">
          免费试用
        </el-button>
      </div>
    </div>
    <div class="bottom">
      <div class="bottom_menu">
        <span>产品</span>
      </div>
      <div class="bottom_menu">
        <span>方案</span>
      </div>
      <div class="bottom_menu">
        <span>案例</span>
      </div>
      <div class="bottom_menu">
        <span>服务</span>
      </div>
      <div class="bottom_menu">
        <span>行业资讯</span>
      </div>
      <div class="bottom_menu">
        <span>招募合作</span>
      </div>
      <div class="bottom_menu">
        <span>关于我们</span>
      </div>
      <div class="bottom_menu">
        <span>开放平台</span>
      </div>
    </div>
  </div>
</template>

<style scoped lang='scss'>
.container{
  width: 100%;
  height: 111px;
  .top{
    display: flex;
    justify-content: space-between;
    align-items: center;
    .top_left{
      margin-left: 10px;
      img{
        width: 100px;
        height: 60px;
      }
    }
    .top_right{
      display: flex;
      justify-content: center;
      align-items: center;
      .top_right_item{
        margin: 0 10px;
        color: #333333;
        font-size: 14px;
      }
      //实现非第一个元素 字体变色
      .top_right_item:not(:nth-child(1)):hover{
        color:red
      }
      .top_button{
        background-color: #CC0000;
        width: 90px;
        height: 40px;
        color: white;
        margin:0 20px;
      }
    }
  }
  //实现展示二维码
  .QrCode_show{
    position:relative;
    .QrCode{
      width: 100px;
      height: 240px;
      padding: 10px 0;
      display: flex;//图片二维码和类型
      background-color:white;
      color: #fff;
      position: absolute;
      top: 100%;
      left: 0;
      opacity: 0;
      visibility: hidden;
      transition: opa、city 0.3s ease-in-out;
    }
  }
  .QrCode_show:hover .QrCode{
    opacity: 1;
    visibility: visible;
  }
  //QrCode左侧样式
  .QrCode_left{
    background-color: #f3efef;
    .QrCode_left_item{
      position: relative;
      display: flex;
      justify-content: start;
      align-items: center;
      height: 40px;
      width: 100px;
      padding-left: 18px;
      //提前加边框解决 hover时候抖动问题
      border-left: 2px solid #f3efef;
      .QrCode_left_item_icon{
        width: 22px;
        height: 22px;
        border-radius: 50%;
        background-color: gray;
        margin: 0 4px;
        //icon居中
        text-align: center;
        line-height: 22px;
      }
      .pic{
        background-color: white;
        width: 240px;
        height: 230px;
        position: absolute;
        top:0;
        left:118px;
        display: none;
        text-align: center;
        padding-top: 10px;
      }

    }
  }
  //icon背景颜色 二维码 暴力
  .QrCode_left_item:nth-child(1):hover{
      border-left: 2px solid red;
      background-color: white;
      //hover时候icon背景颜色改变
      .QrCode_left_item_icon{
        background-color: green;
      }
    .pic{
      display: block;
    }
  }
  .QrCode_left_item:nth-child(2):hover{
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: blue;
    }
    .pic{
      display: block;
      top:-40px
    }
  }
  .QrCode_left_item:nth-child(3):hover{
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: black;
    }
    .pic{
      display: block;
      top:-80px
    }
  }
  .QrCode_left_item:nth-child(4):hover{
    border-left: 2px solid black;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: green;
    }
    .pic{
      display: block;
      top:-80px
    }
  }
  .QrCode_left_item:nth-child(4):hover{
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: green;
    }
    .pic{
      display: block;
      top:-120px
    }
  }
  .QrCode_left_item:nth-child(5):hover{
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: orange;
    }
    .pic{
      display: block;
      top:-160px
    }
  }
  .QrCode_left_item:nth-child(6):hover{
    border-left: 2px solid red;
    background-color: white;
    //hover时候icon背景颜色改变
    .QrCode_left_item_icon{
      background-color: #bc2edc;
    }
    .pic{
      display: block;
      top:-200px
    }

  }

  .bottom{
    width: 100%;
    height: 51px;
    display: flex;
    text-align: center;
    line-height: 51px;
    .bottom_menu{
      margin: 0 20px;
      font-size: 14px;
    }
  }

}
</style>

