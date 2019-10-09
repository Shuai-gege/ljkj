<template>
  <div class="order">
    <navbar title="确认订单" v-if="type!=1"></navbar>
    <navbar title="确认提货单" v-else></navbar>
    <div class="content">
      <!-- 确认订单收货地址 -->
      <div class="site flex" @click="tap" v-if="type!=2">
        <div class="flex_l">
          <van-icon name="location" color="#fc4c4c" size="30px" class="tubiao" />
          <div class="info">
            <p style="font-size:15px;">小阔爱 138xxxxxxxx</p>
            <p>银河系地球村爱神的箭卡时间发货快睡觉都好看阿萨德打请问请问</p>
          </div>
        </div>
        <van-icon name="arrow" size="18px" style="margin-left:5px;" />
      </div>
      <!-- 确认订单信息 -->
      <div class="car">
        <div class="cardateil flex_l">
          <img src="../../image/login.gif" alt />
          <!-- 商品名字、价钱 -->
          <div class="item">
            <p
              style="font-size:15px;color:#333;margin-bottom:5px;"
              class="erhang"
            >泰国新鲜牛油果拉斯柯达啦开始建档立卡</p>
            <p style="color:#FF4444;font-size:15px" class="flex">
              <span>
                ￥
                <b>58.00</b>
              </span>
              <span style="color:#000">x{{num}}</span>
            </p>
          </div>
        </div>
      </div>
      <!-- 订单详细信息 -->
      <van-cell title="购买数量">1件</van-cell>
      <van-cell title="配送方式">快递 免邮</van-cell>
      <div class="flex_r" style="margin:5px">
        <p>
          共{{num}}件
          <span style="color:black;">
            小计：
            <span style="color:#FC4C4C;">￥58.00</span>
          </span>
        </p>
      </div>
    </div>
    <van-submit-bar v-if="type==1" :price="5800" button-text="确认提货" @submit="onSubmit(1)" />
    <van-submit-bar v-if="type==0" :price="5800" button-text="提交订单" @submit="onSubmit(0)" />
    <van-submit-bar v-if="type==2" :price="5800" button-text="加入云仓" @submit="onSubmit(2)" />
    <pay v-if="type!=1" :showpay="showpay" :price="price" @close="closePay"></pay>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
import pay from "@/components/pay";
import { Dialog } from "vant";
export default {
  data() {
    return {
      type: null, //列表类型 0 商城列表  1 本地仓库提货不付钱  2 放入云仓不填地址
      num: "1",
      showpay: false,
      price: "8888"
    };
  },
  components: {
    navbar,
    pay
  },
  mounted() {
    this.type = this.$route.query.type;
    if (this.type != 2) {
      // 先判断有没有收货地址，如果没有提示添加收货地址
      // Dialog.confirm({
      //   title: "请先添加收货地址",
      //   // message: "您可以选择直接购买或放入本地仓库中",
      //   confirmButtonText: "添加地址",
      //   confirmButtonColor: "#fc4c4c",
      //   cancelButtonText: "取消",
      //   cancelButtonColor: "#666"
      // }).then(() => {
      // on confirm
      //   this.$router.push("/add_address");
      // })
      // .catch(() => {
      //   // on cancel
      //   this.$router.go(-1);
      // });
    }
  },
  methods: {
    // 点击提交订单
    onSubmit(type) {
      if (type == 0) {
        // 调提交订单接口
        this.showpay = true;
      } else if (type == 1) {
        // 调提货接口
        this.$router.push({
          path: "/orderList",
          query: {
            orderType: this.type + 1
          }
        });
      } else {
        // 调加入云仓提交订单
        this.showpay = true;
      }
    },
    closePay() {
      this.showpay = false;
      this.$router.push({
        path: "/orderList",
        query: {
          orderType: this.type + 1
        }
      });
    },
    tap() {
      this.$router.push("/address");
    }
  }
};
</script>
<style lang="less" scoped>
.order {
  background: #f5f5f5;
  margin-bottom: 50px;
  .content {
    margin-top: 44px;
    padding: 10px;
    .site {
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 15px;
      background: #fff;
    }
    .tubiao {
      margin-right: 10px;
    }
    .car {
      padding: 5px 10px;
      background-color: #fff;
      width: 100%;
      height: 110px;
      border-radius: 5px 5px 0 0;
      img {
        width: 80px;
        height: 80px;
        margin-top: 10px;
        border-radius: 15px;
      }
      .item {
        flex: 1;
        margin-left: 10px;
      }
    }
  }
}
</style>