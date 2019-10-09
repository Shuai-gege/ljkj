<template>
  <div class="message">
    <!-- 头部公共搜索框 -->
    <tabbar title="消息中心"></tabbar>
    <div class="content">
      <!-- 分割不迷路 -->
      <div class="item flex_l">
        <img src="../../image/彩色/通知.png" alt />
        <div style="flex:1">
          <p class="flex" style="font-size:16px;color:black">
            <span>授权申请通知</span>
            <span style="font-size:12px;color:#c1c1c1">2019.10.07 16:49</span>
          </p>
          <p style="margin-top:5px;">您好，您有一位代理申请授权</p>
        </div>
      </div>
      <!-- 分割不迷路 -->
      <div class="item flex_l">
        <img src="../../image/彩色/通知.png" alt />
        <div style="flex:1">
          <p class="flex" style="font-size:16px;color:black">
            <span>授权申请通知</span>
            <span style="font-size:12px;color:#c1c1c1">2019.10.07 16:49</span>
          </p>
          <p style="margin-top:5px;">您好，您有一位代理申请授权</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  data() {
    return {};
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
.message {
  padding-top: 44px;
  .content {
    .item {
      padding: 10px;
      border-bottom: 1px solid #cecece;
      width: 96%;
      margin: 0 auto;
      img {
        width: 50px;
        height: 50px;
        border-radius: 5px;
        margin-right: 15px;
      }
    }
  }
}
</style>
