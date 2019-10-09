<template>
  <div class="mypurse">
    <navbar title="我的钱包"></navbar>
    <!-- 余额 -->
    <div class="zonge">
      <p>钱包总额（RMB）</p>
      <p style="font-size:30px;">4,000.00</p>
    </div>
    <!-- 可提现，货款，奖金 -->
    <div class="tixian">
      <van-cell title="货款" is-link value="2,900.00" @click="tap(1)" />
      <van-cell title="可提现余额" is-link value="0.00" @click="tap(2)" />
      <van-cell title="奖金" is-link value="1,125.00" @click="tap(3)" />
    </div>
    <p style="margin:10px 0 10px 20px;">更多</p>
    <!-- 收款账号、利润 -->
    <div class="lirun">
      <van-cell title="收款账号设置" is-link to="/myshoukuan" />
      <van-cell title="利润明细" is-link @click="tap(4)" />
    </div>
    <!-- 按钮 -->
    <van-button
      type="primary"
      size="large"
      color="#fc4c4c"
      to="/topup"
      style="margin-bottom:10px;"
    >充值</van-button>

    <van-button
      type="primary"
      size="large"
      color="#F19553"
      to="/tixian"
      style="margin-bottom:30px;"
    >提现</van-button>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      value: 1,
      type: "" //1货款，2奖金可提现余额，3奖金，4利润
    };
  },
  components: {
    navbar
  },
  methods: {
    tap(type) {
      console.log(type);
      this.$router.push({
        path: "/mydetail",
        query: {
          type: type
        }
      });
    }
  }
};
</script>
<style lang="less" scoped>
.mypurse {
  background: #f5f5f5;
  min-height: 100vh;
  padding-top: 45px;
  .zonge {
    margin-top: -1px;
    color: #fff;
    background: #fc4c4c;
    padding: 20px;
  }
  .tixian {
    margin: 10px 0;
  }
  .lirun {
    margin-bottom: 100px;
  }
}
</style>