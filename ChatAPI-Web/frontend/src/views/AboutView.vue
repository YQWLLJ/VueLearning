<template>
  <view-box>
    <!-- 找到我们  图标需要更换 -->
    <div class="content-1">
      <div class="content-1-home">
        <div class="content-1-tittle-wrap">
          <h3>FIND US</h3>
          <div class="content-1-tittle">
            <p>找到我们</p>
            <img src="../assets/标题装饰-1.png">
          </div>
        </div>

        <div class="content-1-mainbox">
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-computer.png">
            </div>
            <div class="banner-text-wrap">
              <h3>桂电北海计算机学院</h3>
              <p>学习优秀，本领过硬。下辖专业：大数据管理与应用、网络工程、网络工程NIIT</p>
              <a href="https://www.guet.edu.cn/gdbh/" target="blank"  class="clickable-link" ></a>

            </div>
          </div>
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-server.png">
            </div>
            <div class="banner-text-wrap">
              <h3>桂电北海网络中心</h3>
              <p>牛人的聚集地，为全校师生提供优质网络技术服务</p>
              <a href="https://www.baidu.com" target="blank"  class="clickable-link"></a>
            </div>
          </div>
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-book_black.png">
            </div>
            <div class="banner-text-wrap">
              <h3>科协优阅网</h3>
              <p>计算机学院科协官网，学院竞赛信息一网打尽</p>
              <a href="https://www.youyue.info" target="blank" class="clickable-link"></a>
            </div>
          </div>
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-gmail_black.png">
            </div>
            <div class="banner-text-wrap">
              <h3>Gmail</h3>
              <p>我们的邮箱</p>
              <a href="https://www.junhaohuang.haoshao@gmail.com"  target="blank" class="clickable-link"></a>
            </div>
          </div>
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-github.png">
            </div>
            <div class="banner-text-wrap">
              <h3>Github</h3>
              <p>我们的代码仓库</p>
              <a href="https://github.com/DamenaShojoBronya" target="blank"  class="clickable-link"></a>
            </div>
          </div>
          <div class="banner">
            <div class="banner-icon-wrap">
              <img src="../assets/icon-wechat_black.png">
            </div>
            <div class="banner-text-wrap">
              <h3>Wechat</h3>
              <p>我们的公众号</p>
              <a href="https://www.baidu.com" target="blank"  class="clickable-link"></a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 使用流程 -->
    <div class="content-3">
      <div class="content-1-home">
        <div class="content-1-tittle-wrap">
          <h3>SERVICE PROVISIONING</h3>
          <div class="content-1-tittle">
            <p>使用流程</p>
            <img src="../assets/标题装饰-1.png">
          </div>
        </div>
        <div class="content-1-mainbox" id="content-3-mainbox">
          <div class="banner3">
            <img src="../assets/图标-使用流程-试用申请.png">
            <h3>申请使用</h3>
            <p>提前提交申请，等待工作人员给予反馈，流程简易</p>
          </div>
          <div class="banner3">
            <img src="../assets/图标-使用流程-登录试用.png">
            <h3>登录使用</h3>
            <p>登录查看了解其内容，可及时接收反馈，和了解到新通知</p>
          </div>
          <div class="banner3">
            <img src="../assets/图标-使用流程-购买服务.png">
            <h3>设备报修</h3>
            <p>有设备故障问题，及时报修，方便简洁，上门服务</p>
          </div>
          <div class="banner3">
            <img src="../assets/图标-使用流程-开启监测.png">
            <h3>审批流程</h3>
            <p>极速接入，可随时查询申请的进度，及时反馈了解情况</p>
          </div>
        </div>
      </div>
    </div>
  </view-box>
</template>

<style scoped>

view-box {
  margin:0 auto;
  margin-top:70px;
  width:100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center
}

.banner {
  position: relative;
  border-radius: 25px 25px;
}
.banner-icon-wrap:after {
  content: "";
  position: absolute;
  background: #f2f3f7;
  border-radius: 12px;
  width:74px;
  height:74px;
  z-index:1;
}
.banner-icon-wrap img{
  width:64px;
  height:64px;
  z-index:2;
}
.banner-text-wrap>a:after {
  width: 20px;
  height: 20px;
  content: "";
  display: block;
  position: absolute;
  bottom: 0;
  right: 0;
  width: 50px;
  height: 50px;
  border-radius: 25px 0;
  cursor: pointer;
  transition: inherit;
  background-color: #69809a;
  background-size: 20px 20px;
  background-repeat: no-repeat;
  background-position: center;
  background-image: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9JzMwMHB4JyB3aWR0aD0nMzAwcHgnICBmaWxsPSIjZmZmZmZmIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGRhdGEtbmFtZT0iTGF5ZXIgMSIgdmlld0JveD0iMCAwIDEwMCAxMDAiIHg9IjBweCIgeT0iMHB4Ij48dGl0bGU+NTI8L3RpdGxlPjxwYXRoIGQ9Ik04MS4zMDMyOSwzOC41MjkzOUExNC4wMTgsMTQuMDE4LDAsMSwwLDYxLjQ3NywxOC43MDY3MUw0Ny4wMDMxNSwzMy4xNzkxNGExNC4wMzAzNywxNC4wMzAzNywwLDAsMCwwLDE5LjgyMTcxLDQuODAxMTMsNC44MDExMywwLDAsMS02Ljc4OTc5LDYuNzg5ODcsMjMuNjQzMjcsMjMuNjQzMjcsMCwwLDEsMC0zMy40MDE0NUw1NC42ODcyMSwxMS45MTY4NEEyMy42MjAzLDIzLjYyMDMsMCwwLDEsODguMDkzMDgsNDUuMzE5MjdMODAuOTIzOCw1Mi40ODcxMWE0LjgwMTE0LDQuODAxMTQsMCwwLDEtNi43ODk4LTYuNzg5ODdaTTExLjkwNzQxLDg4LjA5MzlhMjMuNjUwNTMsMjMuNjUwNTMsMCwwLDAsMzMuNDA1ODYtLjAwMUw1OS43ODY2NCw3My42MjE0N2EyMy42MTU4MywyMy42MTU4MywwLDAsMCwwLTMzLjQwMTQ1LDQuODAxMTQsNC44MDExNCwwLDAsMC02Ljc4OTc5LDYuNzg5ODgsMTQuMDE1MzEsMTQuMDE1MzEsMCwwLDEsMCwxOS44MjI2OEwzOC41MjM0OCw4MS4zMDRBMTQuMDE4LDE0LjAxOCwwLDEsMSwxOC42OTcyLDYxLjQ4MTM1TDI1Ljg2Niw1NC4zMTM1YTQuODAxMTQsNC44MDExNCwwLDAsMC02Ljc4OTgtNi43ODk4N2wtNy4xNjg3OSw3LjE2Nzg1QTIzLjY0NDg5LDIzLjY0NDg5LDAsMCwwLDExLjkwNzQxLDg4LjA5MzlaIj48L3BhdGg+PC9zdmc+);
}
.banner-text-wrap>a:hover::after {
  background-color: #1d71ed;
}

.content-1 {
  width: 100%;
  height: 564px;
  background: #eef2f7;
  min-width: 1400px;
}

.content-1-home {
  width: 1400px;
  margin: auto;
}

.content-1-tittle-wrap {
  height: 126px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* opacity: 0.38; */
  /* background-image:linear-gradient(to bottom,#1d71ed, white); */
}
.content-1-tittle-wrap:after{
  content:"";
  width: 100%;
  height: inherit;
  opacity: 0.38;
  position: relative;
  z-index: 2;

  background-image: radial-gradient(circle farthest-side,#1d71ed, #eef2f7);
}
.content-3 > .content-1-home > .content-1-tittle-wrap:after{
  content:"";
  width: 100%;
  height: inherit;
  opacity: 0.38;
  position: relative;
  z-index: 2;

  background-image: radial-gradient(circle farthest-side,#1d71ed, #FFFFFF);
}
.content-1-tittle-wrap h3 {
  position: absolute;
  z-index: 3;
  opacity: 0.38;
  font-family: 'AlibabaSans-BoldItalic';
  /* 字体倾斜，你考虑一下 */
  font-style:italic;
  font-size: 100px;
  height: inherit;
  letter-spacing: -4px;
  text-align: center;
  color:white;
}

.content-1-tittle {
  position: absolute;
  z-index: 4;
  width: auto;
  height: 34px;
}

.content-1-tittle>p {
  font-family: 'MicrosoftYaHeiUI-Bold';
  font-size: 34px;
  font-weight: bold;
  color: black;
  text-align: center;
  line-height: 34px;
}

.content-1-mainbox {
  height: 398px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  overflow: hidden;
}

.banner {
  width: 386px;
  height: 128px;
  margin: 21px;
  background: #FFFFFF;
  border: 1px solid #DDDDDD;
  display: flex;
  justify-content: center;
  align-items: center;
}

.banner:hover {
  box-shadow: 0 6px 22px 0 rgba(0, 0, 0, 0.18);
  border: 0px;
}

.banner-icon-wrap {
  width: 104px;
  height: 128px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.banner-text-wrap {
  width: 256px;
  height: 90px;
  display: flex;
  justify-content: space-around;
  flex-direction: column;
  /* background: #666666; */
  text-align: center;
}

.banner-text-wrap>h3 {
  margin-left: -50px;
  font-family: 'MicrosoftYaHeiUI-Bold';
  font-size: 30px;
  color: black;
  line-height: 18px;
}

.banner-text-wrap>p {

  margin-top: 10px;
  width: 200px;
  font-family: 'MicrosoftYaHeiUI';
  font-size: 20px;
  color: black;
  line-height: 22px;
  /* background: #5c3939; */
}

.banner:nth-of-type(-n+3)>.banner-text-wrap>h3 {
  font-size: 20px;
}

.banner:nth-of-type(-n+3)>.banner-text-wrap>p {
  font-size: 15px;
}


.content-3 {
  width: 100%;
  height: 433px;
  background: #FFFFFF;
}

#content-3-mainbox {
  height: 307px;
  overflow: hidden;
}

.banner3 {
  width: 126px;
  height: 207px;
  margin: 21px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
}

.banner3>img {
  width: 73px;
  height: 73px;
}

.banner3>h3 {
  font-family: MicrosoftYaHeiUI-Bold;
  font-size: 16px;
  color: #333333;
  text-align: center;
  line-height: 18px;
  /* margin-bottom: 11px; */
}

.banner3>p {
  font-family: MicrosoftYaHeiUI;
  font-size: 14px;
  color: #666666;
  text-align: center;
  line-height: 22px;
}</style>
