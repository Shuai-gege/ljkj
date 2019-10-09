<template>
  <div class="detail">
    <navbar title="可提现明细"></navbar>
    <!-- <div class="yue">
      <p style="color:#333;">可提现余额（RMB）</p>
      <p style="font-size:30px;color:#DB5B28;">0.00</p>
    </div>-->
    <p style="padding:0 0 10px 20px;">更多</p>
    <div class="flex mingxi">
      <div>
        <p>{{name}}</p>
        <p style="font-size:12px;color:#fc4c4c">
          <b>{{name1}}:0.00</b>
        </p>
      </div>
      <div>
        <p>2019-09-30</p>
        <p style="font-size:13px;color:#fc4c4c">-8.50</p>
      </div>
    </div>
    <div class="flex mingxi">
      <div>
        <p>{{name}}</p>
        <p style="font-size:12px;color:#fc4c4c">
          <b>{{name1}}:0.00</b>
        </p>
      </div>
      <div>
        <p>2019-09-30</p>
        <p style="font-size:13px;color:#fc4c4c">-8.50</p>
      </div>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      name: "",
      name1: "",
      type: ""
    };
  },
  components: {
    navbar
  },
  mounted() {
    this.type = this.$route.query.type;
    if (this.type == 1) {
      this.name = "货款";
      this.name1 = "余额";
    } else if (this.type == 2) {
      this.name = "可提现";
      this.name1 = "余额";
    } else if (this.type == 3) {
      this.name = "奖金";
      this.name1 = "余额";
    } else {
      this.name = "利润";
      this.name1 = "利润";
    }
  }
};
</script>
<style lang="less" scoped>
.detail {
  font-size: 14px;
  background: #f5f5f5;
  .yue {
    margin: 55px 0 15px 0;
    padding: 20px;
    background: #fff;
  }
  .mingxi {
    padding: 20px;
    background: #fff;
    margin-bottom: 1px;
  }
}
</style>