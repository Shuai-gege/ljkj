<template>
  <div class="myteam">
    <navbar title="我的团队"></navbar>
    <div class="content">
      <van-tabs v-model="active">
        <van-tab title="我的团队(1)">
          <div class="direct flex_l">
            <img src="../../image/login.gif" alt />
            <div class="txt">
              <p style="color:#333;margin-bottom:10px;">
                代理名字
                <span>(代理级别)</span>
                <van-tag type="warning">发展</van-tag>
              </p>
              <van-icon name="phone" />
              <span>17538146710</span>
            </div>
          </div>
        </van-tab>
        <van-tab title="直接代理(1)">
          <div class="direct flex_l">
            <img src="../../image/login.gif" alt />
            <div class="txt">
              <p style="color:#333;margin-bottom:10px;">
                代理名字
                <span>(代理级别)</span>
                <van-tag type="warning">发展</van-tag>
              </p>
              <van-icon name="phone" />
              <span>17538146710</span>
            </div>
          </div>
        </van-tab>
        <van-tab title="间接代理(1)">
          <div class="direct flex_l">
            <img src="../../image/login.gif" alt />
            <div class="txt">
              <p style="color:#333;margin-bottom:10px;">
                代理名字
                <span>(代理级别)</span>
                <van-tag type="warning">发展</van-tag>
              </p>
              <van-icon name="phone" />
              <span>17538146710</span>
            </div>
          </div>
        </van-tab>
      </van-tabs>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      active: 0,
      type: "" //接受直接代理/简介代理参数
    };
  },
  components: {
    navbar
  },
  mounted() {
    this.type = this.$route.query.type;
    if (this.type == 1) {
      this.active = 1;
    } else if (this.type == 2) {
      this.active = 2;
    } else if (this.type == 0) {
      this.active = 0;
    }
  }
};
</script>
<style lang="less" scoped>
.myteam {
  .content {
    margin-top: 46px;
    background: #e6e6e6;
    .direct {
      background: #fff;
      margin-top: 10px;
      padding: 10px;
      img {
        width: 70px;
        height: 70px;
        border-radius: 10px;
      }
      .txt {
        padding: 10px;
        font-size: 14px;
      }
    }
  }
}
</style>