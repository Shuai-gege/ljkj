<template>
  <div class="shenqing">
    <div class="head1 flex_l">
      <img :src="initdata.invite_user_avatar" alt />
      <div>
        <p>{{initdata.invite_user_name}}（{{initdata.invite_user_agent_name}}）</p>
        <span>邀请你成为“{{initdata.level_name}}”</span>
      </div>
    </div>
    <div class="title">团队</div>
    <div class="head1 flex_l">
      <img :src="initdata.invite_user_team_avatar" alt />
      <div>
        <p>{{initdata.invite_user_team_name}}</p>
      </div>
    </div>
    <div class="title flex">
      <span>授权要求</span>
      <span class="flex_r" @click="$router.push('/shoukuan')">
        查看公司收款账号
        <van-icon name="arrow" />
      </span>
    </div>
    <div class="head1">{{initdata.level_condition}}</div>
    <div class="title">基本信息</div>
    <van-cell-group>
      <van-field v-model="username" clearable label="真实姓名" :placeholder="xingming" />
      <van-field v-model="tel" clearable label="手机号码" :placeholder="dianhua" />
      <!-- <van-field v-model="area" clearable label="地区" placeholder="请选择地区" @click="showArea=true" />
      <van-field v-model="address" clearable label="详细地址" placeholder="街道门牌信息" />-->
    </van-cell-group>
    <div class="title">身份信息</div>
    <van-cell-group>
      <van-field v-model="IDcard" clearable label="身份证号" :placeholder="shenfenzheng" />
      <div class="upload flex">
        <div class="item flex">
          <van-uploader v-model="fan" :after-read="afterRead1" :max-count="1" />
          <img :src="fan" alt />
          <span>头像面</span>
        </div>
        <div class="item flex">
          <van-uploader v-model="zheng" :after-read="afterRead2" :max-count="1" />
          <img :src="zheng" alt />
          <span>国徽面</span>
        </div>
      </div>
    </van-cell-group>
    <div class="title flex">
      <span>支付凭证</span>
      <span class="flex_r" @click="$router.push('/shoukuan')">
        查看公司收款账号
        <van-icon name="arrow" />
      </span>
    </div>
    <van-cell-group>
      <div class="upload1 flex">
        <div class="item flex">
          <van-uploader v-model="fileList" multiple :max-count="3" :after-read="afterRead3" />
          <span>支付凭证（最多三张）</span>
        </div>
      </div>
    </van-cell-group>
    <van-button type="primary" size="large" @click="submit">申请授权</van-button>
    <!-- 地区弹窗 -->
    <!-- <van-action-sheet v-model="showArea">
      <van-area :area-list="areaList" @confirm="confirmArea" />
    </van-action-sheet>-->
  </div>
</template>
<script>
import areaList from "../../common/js/newArea";
import { upload } from "../../common/js/common";
export default {
  data() {
    return {
      username: "",
      // area: "",
      // showArea: false,
      // address: "",
      tel: "",
      areaList,
      IDcard: "",
      id: "",
      initdata: {},
      zheng: [], //身份证
      fan: [], //身份证
      fileList: [], //支付凭证
      xingming: "", //姓名
      dianhua: "", //手机号
      shenfenzheng: "" //身份证
    };
  },

  mounted() {
    if (!localStorage.getItem("token") && !this.$route.query.token) {
      alert(33333333);
      location.href = "http://lj.tieqiao.shop/api/user/wxlogin";
    } else if (!localStorage.getItem("token") && this.$route.query.token) {
      alert(11111111111);
      localStorage.setItem("token", this.$route.query.token);
      this.id = this.$route.query.id;
      this.init();
    } else if (localStorage.getItem("token")) {
      this.id = this.$route.query.id;
      this.init();
    }
  },
  methods: {
    init() {
      this.axios
        .post("/api/agent/inviteAgentInfo", { id: this.id })
        .then(data => {
          this.initdata = data;

          // 判断姓名
          if (data.truename == "") {
            this.xingming = "请输入姓名";
          } else {
            this.xingming = data.truename;
          }
          //判断手机号
          if (data.tel == "") {
            this.dianhua = "请输入手机号";
          } else {
            this.dianhua = data.tel;
          }
          // 判断身份证
          if (data.idcard == "") {
            this.shenfenzheng = "请输入身份证号";
          } else {
            this.shenfenzheng = data.idcard;
          }
          // // 判断身份证正
          // if (data.zheng == []) {
          //   this.zheng = [];
          // } else {
          //   this.zheng = data.front_card_image;
          // }
          // // 判断身份证反
          // if (data.fan == []) {
          //   this.fan = [];
          // } else {
          //   this.fan = data.back_card_image;
          // }
        });
    },
    // 选择地区点击确定
    // confirmArea(area) {
    //   console.log(11111);
    //   this.area = area[0].name + " " + area[1].name + " " + area[2].name;
    //   // this.showArea = false;
    // },
    afterRead1() {
      upload(this.fan[0].content, this.fan[0].file.name).then(data => {
        this.back_card_image = data.url;
      });
    },
    afterRead2() {
      upload(this.zheng[0].content, this.zheng[0].file.name).then(data => {
        this.front_card_image = data.url;
      });
    },
    afterRead3() {
      console.log(this.fileList);
      let payimg = [];
      this.fileList.forEach(item => {
        upload(item.content, item.file.name).then(data => {
          payimg.push(data.url);
          if (payimg.length == this.fileList.length) {
            console.log(payimg);
            this.pay_proof_images = payimg;
          }
        });
      });
    },
    submit() {
      if (!this.username.trim()) {
        this.$toast("请输入姓名");
      } else if (!/^1[3456789]\d{9}$/.test(this.tel)) {
        this.$toast("请输入正确的手机号");
      } else if (!this.IDcard.trim()) {
        this.$toast("请输入身份证号");
      } else if (this.zheng.length == 0) {
        this.$toast("请上传身份证正面");
      } else if (this.fan.length == 0) {
        this.$toast("请上传身份证反面");
      } else if (this.fileList.length == 0) {
        this.$toast("请上传支付凭证");
      } else {
        this.axios
          .post("/api/agent/sbinviteAgent", {
            id: this.id,
            name: this.username,
            tel: this.tel,
            idcard: this.IDcard,
            front_card_image: this.front_card_image,
            back_card_image: this.back_card_image,
            pay_proof_images: this.pay_proof_images.join(",")
          })
          .then(data => {
            this.$toast("申请成功，请耐心等待审核通过");
          });
      }
    }
  }
};
</script>

<style lang="less" scoped>
.shenqing {
  background: #f5f5f5;
  min-height: 100vh;
  color: #333;
  font-size: 14px;
  padding-bottom: 30px;
  .title {
    font-weight: normal;
    color: #666;
    font-size: 13px;
    margin: 8px 12px;
  }
  .upload,
  .upload1 {
    padding: 10px 15px;
    .item {
      flex-direction: column;
      span {
        color: #999;
        font-size: 12px;
      }
    }
  }
  .upload {
    /deep/.van-uploader__upload {
      width: 160px;
      height: 100px;
    }
    /deep/.van-uploader__preview-image {
      width: 160px;
      height: 100px;
    }
  }
  .head1 {
    background-color: #fff;
    padding: 10px;
    img {
      width: 70px;
      height: 70px;
      margin-right: 12px;
      border-radius: 5px;
    }
    span {
      display: block;
      margin-top: 10px;
      color: #999;
      font-size: 13px;
    }
  }
  .van-button {
    display: block;
    margin: 30px auto 0;
    width: 92%;
  }
}
</style>
