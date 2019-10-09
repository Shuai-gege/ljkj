<template>
  <div class="update">
    <!-- 头部公共搜索框 -->
    <tabbar title="我要升级"></tabbar>
    <div class="con">
      <div class="item flex">
        <div class="left">
          <p>普通代理</p>
          <span class="money">需充值金额：100</span>
        </div>
        <van-button type="danger" to="/updateRecord">申请升级</van-button>
      </div>
      <div class="item flex">
        <div class="left">
          <p>联合创始人</p>
          <span class="money">需充值金额：10000</span>
        </div>
        <van-button type="danger" disabled to="/updateRecord">申请升级</van-button>
      </div>
      <div class="item flex">
        <div class="left">
          <p>总代</p>
          <span class="money">需充值金额：10000</span>
        </div>
        <van-button type="danger" :disabled="flag" to="/updateRecord">申请升级</van-button>
      </div>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  data() {
    return {
      type: "", //代理级别
      flag: false
    };
  },
  components: {
    tabbar
  },
  mounted() {
    this.type = this.$route.query.type;
  },
  methods: {}
};
</script>

<style lang="less" scoped>
.update {
  padding-top: 44px;
  background-color: #f5f5f5;
  min-height: 100vh;
  font-size: 16px;
  color: #333;
  .con {
    margin-top: -1px;
    padding: 10px 12px;
    .item {
      background-color: #fff;
      border-radius: 5px;
      padding: 20px 10px;
      margin-bottom: 10px;
      p {
        margin-bottom: 5px;
      }
      .money {
        font-size: 14px;
        color: rgb(247, 135, 8);
      }
    }
  }
}
</style>
