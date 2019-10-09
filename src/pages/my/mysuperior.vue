<template>
  <div class="mysuperior">
    <navbar title="我的上级"></navbar>
    <!-- 我的上级头像 -->
    <div class="touxiang flex_l">
      <img src="../../image/login.gif" alt />
      <div class="superiorname">
        <p style="width:40px;">x先生</p>
        <p>总代</p>
      </div>
      <p style="margin-left:130px;width:130px;">未上传二维码</p>
    </div>
    <!-- 我的上级信息 -->
    <div class="data">
      <van-cell-group>
        <van-field value="无" label="微信号" disabled />
        <van-field value="x先生" label="真实姓名" disabled />
        <van-field value="未知" label="性别" disabled />
        <van-field value="12312312312" label="手机号" disabled />
        <van-field value="xx省xx市xx区" label="地址" disabled />
        <van-field value label="详细地址" disabled />
      </van-cell-group>
    </div>

    <!-- 收款账户信息 -->
    <div class="flex_c">
      <p>暂无收款账户信息</p>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {};
  },
  components: {
    navbar
  }
};
</script>
<style lang="less" scoped>
.mysuperior {
  font-size: 14px;
  background: #f5f5f5;
  .touxiang {
    margin-top: 55px;
    padding: 15px;
    background: #fff;
    img {
      width: 70px;
      height: 70px;
      border-radius: 10px;
    }
    .superiorname {
      padding: 10px;
    }
  }
  .data {
    margin: 7px 0;
  }
  .flex_c {
    background: #fff;
    margin: 7px 0;
  }
}
</style>