<template>
  <div class="topup">
    <navbar title="充值中心"></navbar>
    <p class="shenqing">向品牌方申请</p>
    <van-cell-group>
      <van-field v-model="money" type="text" label="充值金额" placeholder="请输入金额" />
    </van-cell-group>
    <p style="margin-left:15px;">打款时间需与付款凭证上的时间一致</p>
    <van-cell-group>
      <van-field v-model="time" type="text" label="打款时间" placeholder="请输入时间" />
    </van-cell-group>
    <van-cell-group>
      <van-field v-model="message" label="留言" type="textarea" placeholder="请输入留言" rows="2" />
    </van-cell-group>
    <p style="margin-left:15px;">付款凭证</p>
    <div style="background:#fff;padding: 15px;">
      <van-uploader v-model="fileList" multiple />
    </div>
    <div style="padding:20px;">
      <van-button type="primary" size="large" color="#45AA30">提交</van-button>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      fileList: [],
      message: "", //留言
      time: "", //打款时间
      money: "" //充值金额
    };
  },
  components: {
    navbar
  }
};
</script>
<style lang="less" scoped>
.topup {
  font-size: 14px;
  background: #f5f5f5;
  .shenqing {
    margin-top: 55px;
    padding: 15px;
    background: #fff;
    color: #333;
    font-size: 15px;
  }
  .van-cell {
    margin: 20px 0 10px 0;
  }
}
</style>