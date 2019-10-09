<template>
  <div class="ccie">
    <navbar title="授权证书"></navbar>
    <div class="content">
      <img src="../../image/微信图片_20190930101020.jpg" alt />
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
.ccie {
  .content {
    margin-top: 50px;
    img {
      width: 90%;
      height: 90%;
      margin: 0 auto;
      border-radius: 20px;
    }
  }
}
</style>