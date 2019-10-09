<template>
  <div class="invite">
    <!-- 头部公共搜索框 -->
    <tabbar title="邀请代理"></tabbar>
    <div id="canvas" ref="canvas">
      <div class="con">
        <img class="userimg" :src="init.wx_avatar" alt />
        <div class="user">{{init.wx_name}}（{{init.agent_name}}）</div>
        <span>
          邀请你成为{{init.app_name}}的
          <b style="color:#fc4c4c;">{{init.develop_name}}</b>
        </span>
        <img :src="init.file_path" alt class="erweima" />
        <div class="save" @click="savecanvas">
          长按
          <br />保存
        </div>
      </div>
    </div>
    <div class="foot">长按二维码，识别图中二维码，关注公众号后点击微信模板消息链接，录入资料，即可申请代理授权</div>
    <img :src="img" alt />
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
import html2canvas from "html2canvas";
export default {
  data() {
    return {
      level_id: "", //代理id
      init: {},
      img: ""
    };
  },
  components: {
    tabbar
  },
  mounted() {
    this.level_id = this.$route.query.level_id;
    this.axios
      .post("/api/agent/developQrcode", {
        level_id: this.level_id
      })
      .then(data => {
        this.init = data;
      });
  },
  methods: {
    savecanvas() {
      let canvas = document.querySelector(".canvas");
      let that = this;
      html2canvas(canvas, { scale: 2, logging: false, useCORS: true }).then(
        canvas => {
          let ImgSrc = canvas.toDataURL("image/png");
          // var img2 = new Image(); //加载要拼装的图标
          // img2.src = that.init.file_path; //图片的路径
          // img2.crossOrigin = "Anonymous";
          that.img = ImgSrc;
        }
      );
    }
  }
};
</script>

<style lang="less" scoped>
.invite {
  padding-top: 44px;
  color: rgb(241, 65, 65);
  background: linear-gradient(to top, #7f7fd5, #86a8e7, #91eae4);
  min-height: 100vh;
  color: #999;
  font-size: 13px;
  .con {
    background-color: rgb(255, 255, 255);
    width: 80%;
    height: 70vh;
    margin: 10vh auto;
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    position: relative;
    .userimg {
      width: 90px;
      height: 90px;
      border-radius: 50%;
      margin: -60px auto 0;
      border: 3px solid #fff;
    }
    .user {
      font-size: 15px;
      color: #333;
      margin: 20px 0 6px;
    }
    .erweima {
      width: 180px;
      height: 180px;
      position: absolute;
      left: 50%;
      bottom: 50%;
      margin-left: -90px;
      margin-bottom: -100px;
    }
    .save {
      padding-top: 7px;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      color: #fff;
      font-weight: 700;
      font-size: 15px;
      background: linear-gradient(to top, #f7797d, #fbd786);
      position: absolute;
      left: 50%;
      bottom: 20px;
      margin-left: -30px;
    }
  }
  .foot {
    color: #fff;
    margin: -40px 30px 0;
    text-align: center;
  }
}
</style>
