<template>
  <div class="orderDetail">
    <tabbar title="订单详情"></tabbar>
    <div class="detail">
      <van-cell title="用户名" icon="location-o" value="1222222222" />
      <van-cell value="地址金佛is阿吉太供热iOS价格if大家观看电视建安费ID是" class="solo" />
      <div class="con">
        <div class="top flex_l">
          <van-image
            width="2.5rem"
            height="2.5rem"
            fit="contain"
            src="https://img.yzcdn.cn/vant/cat.jpeg"
          />
          <div class="pro">
            <div class="name erhang">商品名字商品名字商品</div>
            <div class="price">
              <i>￥</i>88.00
            </div>
          </div>
        </div>
        <div class="item">
          <van-cell title="运费" value="￥0.00" />
          <van-cell title="订单总价" value="￥58.00" />
          <van-cell class="price" title="实付金额" value="￥58.00" />
        </div>
      </div>
      <div class="con">
        <div class="item">
          <van-cell title="订单编号" value="11556622" />
          <van-cell title="支付方式" value="支付宝" />
          <van-cell title="交易单号" value="11445588776633" />
          <van-cell title="付款时间" value="2019-05-16 10:49:58" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  components: {
    tabbar
  },
  data() {
    return {};
  },
  mounted() {},
  methods: {}
};
</script>
<style lang="less">
.orderDetail {
  margin-top: 44px;
  background-color: #f5f5f5;
  min-height: 93.4vh;
  .detail {
    border-top: 1px solid #f5f5f5;
    .solo {
      margin-top: -10px;
    }
    .con {
      margin: 10px;
      background-color: #fff;
      padding: 10px;
      border-radius: 5px;
      img {
        border-radius: 5px;
        border: 1px solid #f5f5f5;
      }
      .pro {
        flex: 1;
        margin-left: 10px;
        .name {
          font-size: 16px;
          margin-bottom: 10px;
          color: #333;
        }
        .price {
          color: red;
          font-size: 14px;
          i {
            font-size: 10px;
          }
        }
      }
      .item {
        .van-cell {
          margin-top: -8px;
          padding: 7px 0;
          &.price {
            font-size: 16px;
            .van-cell__value {
              color: #fc4c4c;
            }
          }
        }
      }
    }
  }
}
</style>