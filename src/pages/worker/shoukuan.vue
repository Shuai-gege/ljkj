<template>
  <div class="shoukuan">
    <!-- 头部公共搜索框 -->
    <tabbar title="公司收款账户"></tabbar>
    <div class="con">
      <van-tabs v-model="active">
        <van-tab title="微信">
          <div class="item">
            <van-cell title="收款账户类型" value="微信" size="large" />
            <van-cell title="收款人" value="某某某" size="large" />
            <van-cell title="微信号" value="12345675452" size="large" />
            <van-image
              style="margin:30px auto;display:block;"
              width="200"
              height="200"
              src="https://img.yzcdn.cn/vant/cat.jpeg"
            />
          </div>
        </van-tab>
        <van-tab title="支付宝">
          <div class="item">
            <van-cell title="收款账户类型" value="支付宝" size="large" />
            <van-cell title="收款人" value="某某某" size="large" />
            <van-cell title="账号" value="12345565452" size="large" />
            <van-image
              style="margin:30px auto;display:block;"
              width="200"
              height="200"
              src="https://img.yzcdn.cn/vant/cat.jpeg"
            />
          </div>
        </van-tab>
        <van-tab title="银行卡">
          <div class="item">
            <van-cell title="收款账户类型" value="银行卡" size="large" />
            <van-cell title="持卡人" value="某某某" size="large" />
            <van-cell title="卡号" value="1234567894565452" size="large" />
            <van-cell title="银行" value="中国银行" size="large" />
            <van-image
              style="margin:30px auto;display:block;"
              width="200"
              height="200"
              src="https://img.yzcdn.cn/vant/cat.jpeg"
            />
          </div>
        </van-tab>
      </van-tabs>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  data() {
    return {
      active: 0 //默认
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
.shoukuan {
  padding-top: 44px;
  background-color: #f5f5f5;
  min-height: 100vh;
  .con {
    margin-top: -1px;
    .item {
      background-color: #fff;
      margin: 10px 12px;
      padding: 10px;
      border-radius: 5px;
    }
  }
}
</style>
