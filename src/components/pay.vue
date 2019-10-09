<template>
  <div class="pay">
    <!-- 支付方式选择 -->
    <van-popup v-model="showpay" position="bottom" round :style="{ height: '60%' }" @close="close">
      <p class="center title">付款详情</p>
      <div class="price center">{{price}} 元</div>
      <van-radio-group v-model="radio">
        <van-radio class="center" name="1" checked-color="rgb(240, 64, 64)">余额支付</van-radio>
        <van-radio class="center" name="2" checked-color="rgb(240, 64, 64)">货款支付</van-radio>
        <van-radio class="center" name="3" checked-color="rgb(240, 64, 64)">微信支付</van-radio>
        <van-radio class="center" name="4" checked-color="rgb(240, 64, 64)">线下支付</van-radio>
      </van-radio-group>
      <van-button class="button" type="danger" @click="gopay">确认支付</van-button>
    </van-popup>
    <!-- 余额支付密码 -->
    <van-popup
      v-model="showpsd"
      position="bottom"
      round
      :style="{ height: '55%' }"
      @close="closePsd"
    >
      <p class="center title">支付密码</p>
      <van-password-input
        :value="value"
        info="忘记密码"
        :focused="showKeyboard"
        @focus="showKeyboard = true"
      />
      <van-number-keyboard
        :show="showKeyboard"
        @input="onInput"
        @delete="onDelete"
        @blur="showKeyboard = false"
      />
    </van-popup>
  </div>
</template>
<script>
export default {
  data() {
    return {
      radio: "1",
      showpsd: false, //密码弹窗
      value: "", // 密码
      showKeyboard: false //数字键盘
    };
  },
  props: ["showpay", "price"],
  methods: {
    close() {
      this.$emit("close");
    },
    gopay() {
      this.close();
      if (this.radio == 1) {
        // 判断是否设置支付密码和实名认证
        this.showpsd = true;
      } else if (this.radio == 2) {
        // 货款支付
      } else if (this.radio == 3) {
        // 调微信支付
      } else {
        //线下支付
        this.$router.push("/offline");
      }
    },
    closePsd() {
      this.showpsd = false;
    },
    onInput(key) {
      this.value = (this.value + key).slice(0, 6);
      if (this.value.length == 6) {
        this.showpsd = false;
        // 走余额支付
      }
    },
    onDelete() {
      this.value = this.value.slice(0, this.value.length - 1);
    }
  }
};
</script>
<style lang="less">
.pay {
  font-size: 14px;
  color: #333;
  padding: 10px;
  .title {
    height: 40px;
    // border-bottom: 1px solid #f5f5f5;
  }
  .price {
    font-size: 16px;
    color: rgb(240, 64, 64);
    font-weight: 700;
    margin: 15px;
  }
  .van-radio {
    border-bottom: 1px solid #f5f5f5;
    padding: 15px;
  }
  .button {
    width: 90%;
    margin: 30px auto 0;
    display: block;
  }
  .van-password-input__info {
    color: rgb(248, 55, 55);
  }
}
</style>