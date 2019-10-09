<template>
  <div class="record">
    <!-- 头部公共搜索框 -->
    <tabbar title="升级记录"></tabbar>
    <div class="con">
      <van-cell-group>
        <van-cell title="总代" value="审核中" class="solo" />
        <van-cell style="margin-top:-10px;color:#999;" title="申请时间：2019-8-8" value="到期时间：2019-8-8" />
      </van-cell-group>
      <van-cell-group>
        <van-cell title="普通代理" value="审核通过" class="solo" />
        <van-cell style="margin-top:-10px;color:#999;" title="申请时间：2019-8-8" value="到期时间：2019-8-8" />
      </van-cell-group>
      <van-cell-group>
        <van-cell title="普通代理" value="审核中" class="solo" />
        <van-cell style="margin-top:-10px;color:#999;" title="申请时间：2019-8-8" value="到期时间：2019-8-8" />
      </van-cell-group>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  data() {
    return {
      type: "" //代理级别
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
.record {
  .con {
    margin-top: 44px;

    .solo {
      .van-cell__title {
        color: #333;
        font-size: 16px;
      }
      .van-cell__value {
        color: rgb(238, 71, 71);
      }
    }
  }
}
</style>
