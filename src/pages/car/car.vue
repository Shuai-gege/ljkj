<template>
  <div class="money">
    <navbar title="购物车"></navbar>
    <!-- 商品 -->
    <van-swipe-cell class="shangpin" v-for="(item,i) in mylist" :key="i">
      <!--  @click="toDetail(item.goods_id,item.goods_size_id)" -->
      <div class="car">
        <div class="cardateil flex_l">
          <!-- 点击图片勾选 -->
          <van-checkbox v-model="item.checked" checked-color="#fc4c4c" @change="change"></van-checkbox>
          <!-- <img
            :src="item.cover_Image"
            alt
            style="margin-left:3px;"
            @click="toDetail(item.goods_id,item.goods_size_id)"
          />-->
          <van-image
            width="80px"
            height="80px"
            fit="cover"
            :src="item.cover_Image"
            style="margin-left:6px;margin-top:8px;"
            @click="toDetail(item.goods_id,item.goods_size_id)"
          />
          <!-- 商品名字、价钱 -->
          <div class="item">
            <p
              @click="toDetail(item.goods_id,item.goods_size_id)"
              style="font-size:16px;color:#333;margin-bottom:5px;"
              class="yihang"
            >{{item.name}}</p>
            <p style="color:#FF4444;font-size:13px" class="flex">
              <span @click="toDetail(item.goods_id,item.goods_size_id)">
                ￥
                <span style="font-size:17px;margin-left:-3px;">{{item.self_price}}</span>
              </span>
              <van-stepper
                v-model="item.buy_num"
                :max="item.stock"
                @change="changeNum(item.goods_id,item.goods_size_id,item.buy_num)"
              />
            </p>
            <div
              class="size"
              style="margin-top:5px;"
              @click="toDetail(item.goods_id,item.goods_size_id)"
            >
              <i
                style="background:#f5f5f5;padding:2px 8px;border-radius:8px;"
              >{{item.size_name+item.size_value}}</i>
            </div>
          </div>
        </div>
      </div>
      <template slot="right">
        <van-button
          square
          type="danger"
          text="删除"
          class="btn"
          @click="del(i,item.goods_id,item.goods_size_id)"
        />
      </template>
    </van-swipe-cell>

    <!-- 提交订单 -->
    <van-submit-bar :price="price" button-text="提交订单" @submit="onSubmit" class="btm">
      <van-checkbox v-model="checked1" checked-color="#fc4c4c" @click="changeQuan">全选</van-checkbox>
    </van-submit-bar>
  </div>
</template>

<script>
import navbar from "@/components/navbar";
import { Dialog } from "vant";
export default {
  components: {
    navbar
  },
  data() {
    return {
      type: 0, //0 直接购买 2 放入云仓
      checked1: false, //全选
      mylist: [], //列表数据
      price: 0 //总价
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.axios.post("/api/goods/goodsCart").then(data => {
        data.forEach(item => {
          this.$set(item, "checked", false);
        });
        this.mylist = data;
      });
    },
    // 点击复选框时触发，引发全选
    change() {
      let flag = 0;
      this.mylist.forEach(item => {
        if (!item.checked) {
          flag = 1;
          this.checked1 = false;
        }
      });
      if (!flag) {
        this.checked1 = true;
      }
      this.getPrice();
    },
    // 点击全选时触发
    changeQuan() {
      if (!this.checked1) {
        this.mylist.forEach(item => {
          item.checked = true;
        });
      } else {
        this.mylist.forEach(item => {
          item.checked = false;
        });
      }
      this.getPrice();
    },
    //删除
    del(i, goods_id, size_id) {
      Dialog.confirm({
        message: "确定删除吗？"
      })
        .then(() => {
          // 掉接口成功删除
          this.axios
            .post("/api/goods/editCart", {
              goods_id: goods_id,
              size_id: size_id,
              num: 0,
              type: 2
            })
            .then(data => {
              this.$toast("删除成功");
              this.mylist.splice(i, 1);
              this.getPrice();
            });
        })
        .catch(() => {});
    },
    // 提交订单
    onSubmit() {
      Dialog.confirm({
        title: "请选择购买方式",
        message: "您可以选择直接购买或放入本地仓库中",
        confirmButtonText: "直接购买",
        confirmButtonColor: "#fc4c4c",
        cancelButtonText: "加入云仓",
        cancelButtonColor: "#fc4c4c"
      })
        .then(() => {
          // on confirm
          this.type = 0;
          this.$router.push({
            path: "/confirmOrder",
            query: {
              type: this.type
            }
          });
        })
        .catch(() => {
          // on cancel
          this.type = 2;
          this.$router.push({
            path: "/confirmOrder",
            query: {
              type: this.type
            }
          });
        });
    },
    // 改变数量
    changeNum(goods_id, size_id, num) {
      this.getPrice();
      this.axios
        .post("/api/goods/editCart", {
          goods_id: goods_id,
          size_id: size_id,
          num: num,
          type: 2
        })
        .then(data => {});
    },
    // 计算总价格
    getPrice() {
      let price = 0;
      this.mylist.forEach(item => {
        if (item.checked) {
          price += parseFloat(item.self_price) * item.buy_num;
        }
      });
      this.price = price * 100;
    },
    // 详情
    toDetail(goods_id, size_id) {
      this.$router.push({
        path: "/detail",
        query: {
          goods_id: goods_id,
          size_id: size_id
        }
      });
    }
  }
};
</script>

<style scoped lang="less">
.money {
  background: #f5f5f5;
  padding: 44px 10px 100px;
  min-height: 100vh;
  color: #666;

  .car {
    padding: 0 5px;
    background-color: #fff;
    width: 100%;
    height: 110px;
    border-radius: 10px;
    .item {
      flex: 1;
      margin-left: 10px;
    }
  }
  .cardateil {
    padding-top: 7px;
  }
  .btn {
    height: 110px;
    border-radius: 15px;
  }
  .btm {
    margin-bottom: 50px;
  }
  .shangpin {
    margin: 8px 0;
  }
}
</style>
