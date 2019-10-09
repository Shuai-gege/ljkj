<template>
  <div class="teamcenter">
    <navbar title="团队中心"></navbar>
    <div class="person flex_l">
      <img src="../../image/login.gif" alt />
      <div class="txt">
        <p style="color:#333;">
          xxx
          <span>（专注微商管理系统）</span>
        </p>
        <p>口号：无</p>
      </div>
    </div>
    <!-- 收款账户 -->
    <div class="account">
      <van-cell title="公司收款账户" is-link icon="balance-pay" to="/shoukuan" />
    </div>
    <!-- 我的上级。团队 -->
    <div class="my">
      <van-cell title="我的上级" is-link icon="manager-o" to="/mysuperior" />
      <van-cell title="我的团队" is-link icon="friends-o" to="/myteam" />
    </div>
    <!-- 团队活动 -->
    <div class="hot">
      <van-cell title="团队活动" is-link icon="smile-comment-o" />
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
.teamcenter {
  background: #f5f5f5;
  .person {
    margin-top: 60px;
    background: #fff;
    img {
      width: 70px;
      height: 70px;
      margin: 10px;
      border-radius: 10px;
    }
    .txt {
      font-size: 14px;
    }
  }
  .account {
    margin: 15px 0;
    .van-icon-balance-pay:before {
      color: #f1506d;
      font-size: 18px;
    }
  }
  .my {
    margin: 15px 0;
    .van-icon-manager-o:before {
      color: #ce8a56;
      font-size: 18px;
    }
    .van-icon-friends-o:before {
      color: #ce8a56;
      font-size: 18px;
    }
  }
  .van-icon-smile-comment-o:before {
    color: #f0c751;
    font-size: 18px;
  }
}
</style>