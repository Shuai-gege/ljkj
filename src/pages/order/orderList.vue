<template>
  <div class="orderList">
    <tabbar v-if="orderType==1" title="商城订单"></tabbar>
    <tabbar v-else-if="orderType==2" title="提货订单"></tabbar>
    <tabbar v-else title="云仓订单"></tabbar>
    <div class="order">
      <van-tabs v-model="type">
        <van-tab v-if="orderType!=2" title="待付款">
          <div class="item">
            <van-panel title="订单编号：112209033" status="待付款">
              <div class="con" @click="toDetail">
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
                <div class="foot">共1件商品 &nbsp; 实付:￥58.00</div>
              </div>
              <div slot="footer">
                <van-button size="small">取消订单</van-button>
                <van-button size="small" type="danger">付款</van-button>
              </div>
            </van-panel>
          </div>
        </van-tab>
        <van-tab title="待发货" v-if="orderType!=3">
          <div class="item">
            <van-panel title="订单编号：112209033" status="待发货">
              <div class="con" @click="toDetail">
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
                <div class="foot">共1件商品 &nbsp; 实付:￥58.00</div>
              </div>
              <div slot="footer">
                <van-button size="small" @click="backMoney">申请退款</van-button>
                <van-button size="small" type="danger">提醒发货</van-button>
              </div>
            </van-panel>
          </div>
        </van-tab>
        <van-tab title="待收货" v-if="orderType!=3">
          <div class="item">
            <van-panel title="订单编号：112209033" status="待收货">
              <div class="con" @click="toDetail">
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
                <div class="foot">共1件商品 &nbsp; 实付:￥58.00</div>
              </div>
              <div slot="footer">
                <van-button size="small" @click="backMoney">申请退款</van-button>
                <van-button size="small" @click="toWuliu">查看物流</van-button>
                <van-button size="small" type="danger">确认收货</van-button>
              </div>
            </van-panel>
          </div>
        </van-tab>
        <van-tab title="已完成">
          <div class="item">
            <van-panel title="订单编号：112209033" status="已完成">
              <div class="con" @click="toDetail">
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
                <div class="foot">共1件商品 &nbsp; 实付:￥58.00</div>
              </div>
              <div slot="footer">
                <!-- <van-button size="small">取消订单</van-button> -->
                <van-button size="small" type="danger">删除订单</van-button>
              </div>
            </van-panel>
          </div>
        </van-tab>
      </van-tabs>
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
    return {
      orderType: 0 //订单类型  1 商城订单  2 提货订单  3 云仓订单
    };
  },
  mounted() {
    this.orderType = this.$route.query.orderType;
  },
  methods: {
    toWuliu() {
      this.$router.push({
        path: "/wuliu",
        query: {
          order_id: 1
        }
      });
    },
    toDetail() {
      this.$router.push({
        path: "/orderDetail",
        query: {
          order_id: 1
        }
      });
    },
    backMoney() {
      this.$router.push({
        path: "/backMoney",
        query: {
          order_id: 1
        }
      });
    }
  }
};
</script>
<style lang="less">
.order {
  margin-top: 44px;
  background-color: #f5f5f5;
  min-height: 100vh;
  .item {
    margin: 12px;
    .van-cell {
      border-radius: 6px;
    }
    .van-cell-group {
      border-radius: 6px;
    }
    .con {
      margin-top: -1px;
      padding: 10px;
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
      .foot {
        margin-top: 5px;
        text-align: right;
      }
    }
    .van-panel__footer {
      width: 100%;
      display: flex;
      justify-content: flex-end;
    }
  }
}
</style>