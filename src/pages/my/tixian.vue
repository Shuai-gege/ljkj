<template>
  <div class="tixian">
    <navbar title="提现"></navbar>
    <!-- 选择提现到哪里 -->
    <div class="xuanze">
      <van-action-sheet
        v-model="show"
        :actions="actions"
        cancel-text="取消"
        @select="onSelect"
        @cancel="onCancel"
      />
      <van-cell :title="type" size="large" label="xxxxxx" is-link @click="xuanze" />
      <!-- 提现金额 -->
      <van-cell-group>
        <van-field
          style="padding-left:20px;height:80px;line-height:60px;font-size:18px;"
          placeholder="请输入提现金额"
          left-icon="gold-coin-o"
        />
      </van-cell-group>
      <!-- 按钮 -->
      <van-button type="danger" size="large" style="margin-top:100px;">提现</van-button>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      show: false,
      actions: [{ name: "银行卡" }, { name: "支付宝" }],
      type: "银行卡"
    };
  },
  components: {
    navbar
  },
  methods: {
    onSelect(item) {
      // 点击选项时默认不会关闭菜单，可以手动关闭
      this.show = false;
      this.type = item.name;
      //   this.$toast(item.name);
    },
    onCancel() {},
    xuanze() {
      this.show = true;
    }
  }
};
</script>
<style lang="less" scoped>
.tixian {
  .xuanze {
    margin-top: 55px;
  }
  /deep/ i {
    font-size: 20px;
  }
}
</style>